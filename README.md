 ## Users

| Attribute | Data Type | Description | Contraints |
|---|---|---|---|
| userId | serial | ตัวเลขที่ระบุผู้ใช้ โดยที่แต่ละผู้ใช้จะไม่ซ้ำกัน | Primary Key |
| name | varchar (255) | ชื่อ นามสกุล ผู้ใช้ | Not Null |
| username | varchar (255) | ชื่อผู้ใช้ | Not Null |
| password | varchar (255) | รหัสผู้ใช้ | Not Null |
| birthbay | date | วัน เดือน ปี เกิด ของผู้ใช้ | Not Null |

## Rides
| Attribute | Data Type | Description | Contraints |
|---|---|---|---|
| rideId | serial | ตัวเลขที่ระบุเครื่องเล่นแต่ละเครื่องเล่น โดยที่แต่ละเครื่องเล่นไม่ซ้ำกัน | Primary Key |
| name | varchar (255) | ชื่อเครื่องเล่น | Not Null |
| detail | varchar (255) | รายละเอียดของเครื่องเล่น | Not Null |
| priceChildren | integer | ราคาเครื่องเล่น ที่เป็นราคาเด็ก | Not Null |
| priceAdult | integer | ราคาเครื่องเล่น ที่เป็นราคาผู้ใหญ่ | Not Null |
| priceSenior | integer | ราคาเครื่องเล่น ที่เป็นราคาสูงวัย | Not Null |
| fastPassRate | integer | อัตราค่าบริการที่เพิ่มราคาตั๋วของผู้ใช้ | Not Null |
| image | varchar (255) | Path ของรูปภาพ  | Not Null |

## TicketType
| Attribute | Description |
|---|---|
| Children | เด็ก |
| Adult | ผู้ใหญ่ |
| Senior | ผู้สูงวัย |
