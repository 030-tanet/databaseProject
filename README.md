## Users
| Attribute | Data Type | Description | Contraints |
|---|---|---|---|
| userId | serial | ตัวเลขที่ระบุผู้ใช้ โดยที่แต่ละผู้ใช้จะไม่ซ้ำกัน (ระบบสร้างเอง) | Primary Key |
| name | varchar (255) | ชื่อ นามสกุล ผู้ใช้ (ผู้ใช้กรอก) | Not Null |
| username | varchar (255) | ชื่อผู้ใช้ (ผู้ใช้กรอก) | Not Null |
| password | varchar (255) | รหัสผู้ใช้ (ผู้ใช้กรอก) | Not Null |
| birthbay | date | วัน เดือน ปี เกิด ของผู้ใช้ (ผู้ใช้กรอก) | Not Null |
 
## Rides
| Attribute | Data Type | Description | Contraints |
|---|---|---|---|
| rideId | serial | ตัวเลขที่ระบุเครื่องเล่นแต่ละเครื่องเล่น โดยที่แต่ละเครื่องเล่นไม่ซ้ำกัน (ระบบสร้างเอง) | Primary Key |
| name | varchar (255) | ชื่อเครื่องเล่น (ระบบสร้างเอง) | Not Null |
| detail | varchar (255) | รายละเอียดของเครื่องเล่น (ระบบสร้างเอง)| Not Null |
| priceChildren | integer | ราคาเครื่องเล่น ที่เป็นราคาเด็ก (ระบบสร้างเอง) | Not Null |
| priceAdult | integer | ราคาเครื่องเล่น ที่เป็นราคาผู้ใหญ่ (ระบบสร้างเอง) | Not Null |
| priceSenior | integer | ราคาเครื่องเล่น ที่เป็นราคาสูงวัย (ระบบสร้างเอง) | Not Null |
| fastPassRate | integer | อัตราค่าบริการที่เพิ่มราคาตั๋วของผู้ใช้ (ระบบสร้างเอง) | Not Null |
| image | varchar (255) | Path ของรูปภาพ (ระบบสร้างเอง) | Not Null |
| shortDes | varchar(255)[] | list ของคำอธิบายสั้นๆ ของเครื่องเล่น (ระบบสร้างเอง) | Not Null |

## Bookings
| Attribute | Data Type | Description | Contraints |
|---|---|---|---|
| bookingId | serial | ตัวเลขที่ระบุการจอง โดยที่แต่ละการจองไม่ซ้ำกัน (ระบบสร้างเอง) | Primary Key | 
| userId | integer | userId ของผู้ใช้ที่ทำการจอง (ระบบดึงมา) | Foreign Key, Not Null |
| amountChildren | integer | จำนวนตั๋วของเด็ก (ผู้ใช้กรอก) | Not Null |
| amountAdult | integer | จำนวนตั๋วของผู้ใหญ่ (ผู้ใช้กรอก) | Not Null |
| amountSenior | integer | จำนวนตั๋วของผู้สูง (ผู้ใช้กรอก) | Not Null |
| rideId | integer | rideId ของเครื่องเล่นที่ถูกจอง (ระบบดึงมา) | Foreign Key, Not Null |
| isFastPass | boolen | ค่าความจริงบอกว่าผู้ใช้ต้องการ fastpass หรือไม่ โดยที่ true คือ ผู้ใช้ต้องการ fastpass และ false คือ ผู้ใช้ไม่ต้องการ fastpass (ผู้ใช้กรอก) | Not Null |
| bookingDate | timestamp | วัน/เดือน/ปี ที่ผู้ใช้ต้องการจอง(วันที่ต้องการเข้าไปเล่น) (ผู้ใช้กรอก) | Not Null |
| discountId | integer | discountId ของโค้ดลดราคา (ระบบดึงมา) | Foreign Key, Null|
| payment | boolen | ราคาของการจองนี้ (ผู้ใช้กรอก) | Not Null |
| createdAt | timestamp |  วัน/เดือน/ปี ที่สร้างการจองนี้ (ระบบสร้างเอง) | Default current_timestamp |
| updateAt | timestamp |  วัน/เดือน/ปี ที่แก้ไขการจองนี้ (ระบบสร้างเอง) | Default current_timestamp |

## Discounts
| Attribute | Data Type | Description | Contraints |
|---|---|---|---|
| discountId | serial | ตัวเลขที่ระบุโค้ดลดราคา โดยที่แต่ละโค้ดไม่ซ้ำกัน (ระบบสร้างดึง) | Primary Key |
| code | varcha (30) | โค้ดลดราคา (ระบบสร้างเอง) | Not Null |
| priceDiscount | integer | จำนวนราคาที่ส่วนลดลดไป (ระบบบดึงมา) | Not Null |
| minPrice | integer | ราคาขั้นต่ำที่สามารถใช้ส่วนลดได้ (ระบบสร้างเอง) | Not Null |
| usagelimit | integer | จำนวนครั้งที่มากที่สุดที่สามารถใช้ส่วนลดนี้ได้ (ระบบสร้างเอง) | Not Null |
| usedCount | integer | จำนวนครั้งที่ส่วนลดนี้ถูกใช้ไปแล้ว (ระบบสร้างเอง) | Not Null |
