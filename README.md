I do the scan sucessfully, i had to deal with some errors

A. 
Error: Resource not accessible by integration - https://docs.github.com/rest/actions/workflow-runs#get-a-workflow-run
Warning: Failed to gather information for telemetry: Resource not accessible by integration - https://docs.github.com/rest/actions/workflow-runs#get-a-workflow-run. Will skip sending status report.

This error usually happens because the GitHub Actions GITHUB_TOKEN doesn't have high enough permissions to "write" the security report back to your repository's Security tab.

Basically, the scan finished successfully, but it's being blocked from saving the results where you can see them.

How to Fix the Permissions
You need to adjust the settings in your checkov.yml file. Update the permissions block to ensure it looks exactly like this:


permissions:
      contents: read
      security-events: write
      actions: read      # <--- Add this line






    B   Error 2
       Warning: Code scanning is not enabled for this repository. Please enable code scanning in the repository settings. - https://docs.github.com/rest
  Error: Please verify that the necessary features are enabled: Code scanning is not enabled for this repository. Please enable code scanning in the repository settings. - https://docs.github.com/rest


Solved it by using the following references

1. https://docs.github.com/en/code-security/concepts/code-scanning/setup-types
<img width="1354" height="524" alt="image" src="https://github.com/user-attachments/assets/cef17274-3054-4a49-918b-e723f90d3a19" />

2. https://docs.github.com/en/code-security/how-tos/scan-code-for-vulnerabilities/configure-code-scanning/configuring-default-setup-for-code-scanning

3. ![Uploading image.png…]()
