# python_project
Prerequisites:
    1.Install Docker SDK for Python: You’ll need the Docker SDK for Python to interact with Docker images.
       by using this command :-  "pip install docker"
    
    
    2.Install Trivy on your machine for scanning container images. If you don't have Trivy installed, you can install it shown below:
    
    For Linux command:- "sudo apt install trivy"
    
    For Docker:-  "docker run --rm -v /var/run/docker.sock:/var/run/docker.sock aquasec/trivy image python"
    
    
    
Running the Script:
  Make sure that Docker and Trivy are installed on your system.
  Save the code in a file, e.g., container_security_scanner.py.
  Run the script:- "python3 container_security_scanner.py"


Extending the Script:
    Filter Vulnerabilities: You can extend the script to filter vulnerabilities based on severity (e.g., only show HIGH or 
                            CRITICAL vulnerabilities).
    Report Generation: Add functionality to save scan results to a file or send them via email.
    CI/CD Integration: This scanner can be integrated into a CI/CD pipeline to automatically scan container images before 
                       deployment.

