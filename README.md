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
| shortDes | varchar(255)[] | list ของคำอธิบายสั้นๆ ของเครื่องเล่น | Not Null |

## TicketType
| Attribute | Description |
|---|---|
| Children | เด็ก |
| Adult | ผู้ใหญ่ |
| Senior | ผู้สูงวัย |

## Bookings
| Attribute | Data Type | Description | Contraints |
|---|---|---|---|
| bookingId | serial | ตัวเลขที่ระบุการจอง โดยที่แต่ละการจองไม่ซ้ำกัน | Primary Key | 
| userId | integer | userId ของผู้ใช้ที่ทำการจอง | Foreign Key, Not Null |
| ticket | TicketType | ประเภทของตั๋ว | Not Null |
| amount | integer | จำนวนตั๋วที่ผู้ใช้ต้องการ | Not Null |
| rideId | integer | rideId ของเครื่องเล่นที่ถูกจอง | Foreign Key, Not Null |
| isFastPass | boolen | ค่าความจริงบอกว่าผู้ใช้ต้องการ fastpass หรือไม่ โดยที่ true คือ ผู้ใช้ต้องการ fastpass และ false คือ ผู้ใช้ไม่ต้องการ fastpass | Not Null |
| bookingDate | timestamp | วัน/เดือน/ปี ที่ผู้ใช้ต้องการจอง(วันที่ต้องการเข้าไปเล่น) | Not Null |
| discountId | integer | discountId ของโค้ดลดราคา | Not Null |
| payment | boolen | ราคาของการจองนี้ | Not Null |
| createdAt | timestamp |  วัน/เดือน/ปี ที่สร้างการจองนี้ | Default current_timestamp |
| updateAt | timestamp |  วัน/เดือน/ปี ที่แก้ไขการจองนี้ | Default current_timestamp |

## Discounts
| Attribute | Data Type | Description | Contraints |
|---|---|---|---|
| discountId | serial | ตัวเลขที่ระบุโค้ดลดราคา โดยที่แต่ละโค้ดไม่ซ้ำกัน | Primary Key |
| code | varcha (30) | โค้ดลดราคา | Not Null |
| priceDiscount | integer | จำนวนราคาที่ส่วนลดลดไป | Not Null |
| usagelimmit | integer | จำนวนครั้งที่มากที่สุดที่สามารถใช้ส่วนลดนี้ได้ | Not Null |
| usedCount | integer | จำนวนครั้งที่ส่วนลดนี้ถูกใช้ไปแล้ว | Not Null |
