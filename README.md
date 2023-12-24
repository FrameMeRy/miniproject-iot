1q2w3e4r
# ชื่อโครงการ: BB Payment (bangbank)

## สมาชิกในกลุ่ม
- 64120280 รัชชานนท์ ชูเกียรติเถกิง 
- 64102288 จิรายุ สาสนทาญาติ 
- 64117039 ทีปกร ตระกูลกลกิจ

## บทนำ
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ทางกลุ่มผู้จัดทำโครงการสนใจเรื่องระบบชำระเงินผ่านบัตรและความสะดวกสบายของมนุษย์ ซึ่งการชำระเงินผ่านบัตรจะช่วยอำนวยความสะดวกสบายให้กับมนุษย์โดยจะเพิ่มความรวดเร็วให้กับการซื้อขายต่างๆเพื่อเป็นแนวทางการลดขั้นตอนและเพิ่มความรวดเร็วให้กับการซื้อขาย
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;เนื่องด้วยปัจจุบันมนุษย์นั้นมีจำนวนมากขึ้นส่งผลให้สถานที่ที่มีขนาดจำกัดอัดแน่ไปด้วยมนุษย์หากเกิดความล่าช้าในกระบวนการต่างๆส่งผลให้มนุษย์นั้นไม่สะดวกสบาย ดั้งนั้นผู้จัดทำจึงมุ่งเน้นในการผลิตอุปกรณ์ IoT ที่สามารถลดขั้นตอนกระบวนการการซื้อ ขายเพื่อเป็นหนึ่งในตัวช่วยในการลดกระบวนการและเพิ่มความรวดเร็วให้กับกระบวนการดังกล่าว
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ทางผู้จัดทำโครงงานจึงพัฒนาอุปกรณ์ IoT ที่สามารถชำระเงินผ่านระบบRFID โดยมีข้อมูลที่เก็บเป็นชื่อของผู้ใช้บัตร จำนวนเงิน ไอดี และส่วนที่เป็นสิ้นค้าจะมีชื่อสินค้า ราคา

## การออกแบบระบบ
### Data Stucture
โครงสร้างข้อมูลจะถูกจัดเก้บในส่วนของ Json ที่จะประกอบไปด้วยข้อมูล 2 ส่วนของโดยจะส่วนของบัตรมีดังนี้ id,Name,Money และช่วนของสิ้นค้ามีดังนี้ id,Pname,Price ดังตัวอย่างตามลำดับ

#### ส่วนของบัตร (CInformation):
```json
{
    "CInformation": [
        {
            "id": 1,
            "Name": "Frame",
            "Money": 300
        },
        {
            "id": 2,
            "Name": "Bank",
            "Money": 300
        }
    ]
}

```

### Data Dictionary

| Attribute | Description | Data Type | Example |
|--------------------|--------------------|--------------------|--------------------|
| id  | id ของผู้ใช้งาน  | int   | 1   |
| Name  |  ชื่อของผู้ใช้  | String   | bang   |
| Money  |เงินของผู้ใช้  | int   | 100   |

## การพัฒนาระบบ
## การทดสอบ   
## สรุปผมการทดสอบ



