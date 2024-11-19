Script to Scan Logs Static Ones

```bash
#!/bin/bash

# Define an array of log file paths for WSL
logFilePaths=(
    "/mnt/c/Users/rifat.sahin/Downloads/main.log"
    "/mnt/c/Users/rifat.sahin/Downloads/sublog1.log"
    "/mnt/c/Users/rifat.sahin/Downloads/sublog2.log"
    "/mnt/c/Users/rifat.sahin/Downloads/sublog3.log"
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
```

### Changes Made:
1. **Quoting Variables**: Added quotes around variables to handle paths or filenames with spaces.
2. **Date Parsing**: Ensured the date parsing is consistent and correct.
3. **Comments**: Improved comments for clarity.

---
# With Kubernetes

```bash
#!/bin/bash

# Define an array of pod names and container names
pods=(
    "pod1 container1"
    "pod2 container2"
    "pod3 container3"
)

# Function to extract and display metadata entries with pod names and dates
extract_metadata() {
    local podName=$1
    local containerName=$2
    local oneDayAgo=$(date -d '1 day ago' +%s)
    kubectl logs "$podName" -c "$containerName" | grep "mymetadata" | while read -r line; do
        if [[ $line =~ ts=([0-9T:-]+) ]]; then
            logDate="${BASH_REMATCH[1]}"
            logDateEpoch=$(date -d "$logDate" +%s)
            if (( logDateEpoch >= oneDayAgo )); then
                if [[ $line =~ my=([^/]+) ]]; then
                    mymetadata="${BASH_REMATCH[1]}"
                    echo "pod=$podName container=$containerName logdate=$logDate mymetadata=$mymetadata"
                fi
            fi
        fi
    done | sort | uniq
}

# Display results for each pod and container
for pod in "${pods[@]}"; do
    podName=$(echo $pod | awk '{print $1}')
    containerName=$(echo $pod | awk '{print $2}')
    echo "Results for pod $podName, container $containerName:"
    extract_metadata "$podName" "$containerName"
done
```

In this script:
- The `pods` array contains pairs of pod names and container names.
- The `extract_metadata` function uses `kubectl logs` to fetch logs from the specified pod and container.
- The rest of the script processes the logs similarly to your original script, extracting and displaying metadata entries.

Feel free to adjust the pod and container names in the `pods` array as needed. Let me know if you need any further assistance!
