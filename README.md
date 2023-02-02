
import csv

def aggregate_data(input_files, output_file):
    data = []
    for input_file in input_files:
        with open(input_file, 'r') as f:
            reader = csv.DictReader(f, delimiter='\t')
            data.extend(list(reader))
    with open(output_file, 'w') as f:
        writer = csv.DictWriter(f, fieldnames=["id", "username", "email", "password", "plain_password","ip_address"], delimiter='\t')
        writer.writeheader()
        for row in data:
            writer.writerow(row)

input_files = [
    "user_email_hash.1m.tsv",
    "plain_32m.tsv",
    "ip_1m.tsv"
   
]
output_file = "output.tsv"
aggregate_data(input_files, output_file)
