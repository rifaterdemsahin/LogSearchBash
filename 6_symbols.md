#!/bin/bash

# Define an array of log file paths
logFilePaths=(
    "/mnt/c/Users/rifat.sahin/Downloads/main.log"
    "/mnt/c/Users/rifat.sahin/Downloads/cluster1.log"
    "/mnt/c/Users/rifat.sahin/Downloads/cluster2.log"
    "/mnt/c/Users/rifat.sahin/Downloads/cluster3.log"
)

# Function to extract and display metadata entries with log file names and dates
# mymetadata is any unique text that is log line based unique
extract_metadata() {
    local logFilePath=$1
    local oneDayAgo=$(date -d '1 day ago' +%s)
    grep "mymetadata" "$logFilePath" | while read -r line; do
        if [[ $line =~ ts=([0-9T:-]+) ]]; then
            logDate="${BASH_REMATCH[1]}"
            logDateEpoch=$(date -d "$logDate" +%s)
            if (( logDateEpoch >= oneDayAgo )); then
                if [[ $line =~ my=([^/]+) ]]; then
                    mymetadata="${BASH_REMATCH[1]}"
                    echo "logfile=$(basename "$logFilePath") logdate=$logDate mymetadata=$mymetadata"
                fi
            fi
        fi
    done | sort | uniq
}

# Display results for each log file
for logFilePath in "${logFilePaths[@]}"; do
    echo "Results for $(basename "$logFilePath"):"
    extract_metadata "$logFilePath"
done