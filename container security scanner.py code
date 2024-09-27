import docker
import subprocess

class ContainerSecurityScanner:
    def __init__(self):
        # Initialize Docker client
        self.client = docker.from_env()

    def pull_image(self, image_name):
        """
        Pulls a Docker image from a registry.
        :param image_name: Name of the Docker image to pull (e.g., 'python:3.8-slim').
        :return: Docker image object.
        """
        try:
            print(f"Pulling image {image_name}...")
            image = self.client.images.pull(image_name)
            print(f"Successfully pulled image: {image_name}")
            return image
        except Exception as e:
            print(f"Error pulling image {image_name}: {str(e)}")
            return None

    def scan_image(self, image_name):
        """
        Scans a Docker image for vulnerabilities using Trivy.
        :param image_name: Name of the Docker image to scan.
        """
        try:
            print(f"Scanning {image_name} for vulnerabilities...")
            result = subprocess.run(['trivy', 'image', image_name], check=True, stdout=subprocess.PIPE, stderr=subprocess.PIPE)
            print(result.stdout.decode('utf-8'))
        except subprocess.CalledProcessError as e:
            print(f"Error scanning image {image_name}: {e.stderr.decode('utf-8')}")

    def run_scan(self, image_name):
        """
        Orchestrates the entire process: pulling the image and scanning it.
        :param image_name: Name of the Docker image to scan.
        """
        # Step 1: Pull Docker image
        image = self.pull_image(image_name)

        if image:
            # Step 2: Scan the Docker image for vulnerabilities
            self.scan_image(image_name)


if __name__ == "__main__":
    # Create an instance of the security scanner
    scanner = ContainerSecurityScanner()

    # Example Docker image to scan
    docker_image = 'python:3.8-slim'

    # Run the scanning process
    scanner.run_scan(docker_image)

