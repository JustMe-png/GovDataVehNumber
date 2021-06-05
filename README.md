# Gov Data Vehicle Number
Search vehicle info by vehicle number <i>(<strong>mispar_rechev</strong>)</i> (<strong>Python 3.9</strong>)
- <a href="https://info.data.gov.il/datagov/home/">מאגרי המידע הממשלתיים</a>
- <a href="https://www.gov.il/he/Departments/DynamicCollectors/private-and-commercial-vehicles">מספרי רישוי של כלי רכב פרטיים ומסחריים</a>
  
  
```python
import requests
import json

veh_number = input("Enter mispar rechev (vehicle number): ")

veh_request_json={"DynamicTemplateID":"af3b0f3e-7b99-4a3f-a9cf-15e02384fe1c","QueryFilters":{"skip":{"Query":"0"},"mispar_rechev":{"Query":veh_number}},"From":"0"}

data = requests.post("https://www.gov.il/he/api/DataGovProxy/GetDGResults", json=veh_request_json)

value = json.loads(data.text)
tozeret_nm = value['Results'][0]['Data']['tozeret_nm']
kinuy_mishari = value['Results'][0]['Data']['kinuy_mishari']
shnat_yitzur = value['Results'][0]['Data']['shnat_yitzur']
baalut =  value['Results'][0]['Data']['baalut']
tzeva_rechev = value['Results'][0]['Data']['tzeva_rechev']

print("שם תוצר: " + tozeret_nm)
print("כינוי מסחרי: " + kinuy_mishari)
print("שנת ייצור: " + shnat_yitzur)
print("בעלות נוכחית: " + baalut)
print("צבע רכב: " + tzeva_rechev)
```

  
## Scheme
![Scheme](https://i.imgur.com/KrXemLr.gif)
  
  
