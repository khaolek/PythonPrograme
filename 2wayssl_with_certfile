# -*- coding: utf-8 -*-
# encoding: utf-8
import requests
import json

clientId = "clientId"
baseCertPath = "./filecert/"
urlEndpoint = "https://paymentgateway.bank.com:7334"

path_to_bank_pem_file = f"{filecert}/bankcert/banktest.cer"
path_to_crt_file = f"{baseCertPath}CertPFX2023.crt"
path_to_key_file = f"{baseCertPath}CertPFX2023.pem"

payload = json.dumps({
    "servCode": clientId,
    "receiType": "BANKAC",
    "receibookno": "1900016666",
    "amount": "100.00",
    "additionalRef": ""
})
print(f"payload >\n{payload}")
headers = {
    'Request-Ref': 'c04a8e69b5d4d.....32fc7d430',
    'Transmit-Date-Time': '2023-09-10T16:41:10.234+07:00',
    'Authorization': 'Basic asfsafsafkasfoajsfaisfoasafa...asofs',
    'Content-Type': 'application/json',
    'Signature': 'k+dfadsldkaafsY7nasfsafdU3fDdpb/LH...Jmn1xHKw=='
}
cert_file = (path_to_crt_file, path_to_key_file)
session = requests.Session()
response = session.request("POST",
                            urlEndpoint,
                            headers=headers,
                            data=payload,
                            verify=path_to_bank_pem_file,
                           cert=cert_file)

print("headers > ", response.headers)
print("status_code > ", response.status_code)

try:
    print("body json > ", response.json())
except ValueError:
    print("body text > ", response.text)

