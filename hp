import requests
import zipfile
import os
import requests
import shutil

def download_and_extract():
    # Step 1: Download the zip file
    url = "https://zip.baipiao.eu.org/"
    response = requests.get(url)
    zip_file_path = "reversedIp.zip"

    with open(zip_file_path, "wb") as file:
        file.write(response.content)

    # Step 2: Extract the files from the zip
    extracted_files_dir = "./extracted_files/"
    os.makedirs(extracted_files_dir, exist_ok=True)

    with zipfile.ZipFile(zip_file_path, "r") as zip_ref:
        zip_ref.extractall(extracted_files_dir)

    # Step 3: Combine the text files into one file
    combined_file_path = "pr_ip.txt"

    with open(combined_file_path, "w") as combined_file:
        for root, dirs, files in os.walk(extracted_files_dir):
            for file in files:
                if file.endswith(".txt"):
                    file_path = os.path.join(root, file)
                    if "-80." in file or "-443." in file:
                        print(file, file_path)
                        with open(file_path, "r") as txt_file:
                            combined_file.write(txt_file.read())
                        
# Run the task once at the beginning
download_and_extract()
