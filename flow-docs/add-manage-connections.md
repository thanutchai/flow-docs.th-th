---
title: เรียนรู้เกี่ยวกับการเชื่อมต่อกับข้อมูลของคุณโดยใช้เกตเวย์การเชื่อมต่อและข้อมูลภายในองค์กร | Microsoft Docs
description: เพิ่มหรือจัดการการเชื่อมต่อกับ SharePoint, SQL Server, OneDrive for Business, Salesforce, Office 365, OneDrive, Dropbox, Twitter, Google Drive และอื่น ๆ
services: ''
suite: flow
documentationcenter: na
author: stepsic-microsoft-com
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/15/2017
ms.author: stepsic
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: bdfa1072bca2afc7c608a4dbf68b8f598dff89f1
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: th-TH
ms.lasthandoff: 09/12/2018
ms.locfileid: "44689122"
---
# <a name="manage-connections-in-microsoft-flow"></a>จัดการการเชื่อมต่อใน Microsoft Flow
ถ้าคุณสร้างการเชื่อมต่อใน Microsoft Flow คุณสามารถเข้าถึงข้อมูลของคุณขณะสร้างโฟลว์ได้ Microsoft Flow รวมการเชื่อมต่อที่ใช้กันทั่วไป รวมถึง SharePoint, SQL Server, Office 365, OneDrive for Business, Salesforce, Excel, Dropbox, Twitter และอื่น ๆ การเชื่อมต่อจะแชร์ร่วมกับ PowerApps ดังนั้นเมื่อคุณสร้างการเชื่อมต่อในหนึ่งผลิตภัณฑ์ การเชื่อมต่อนั้นจะปรากฏขึ้นในผลิตภัณฑ์อื่น

ตัวอย่างเช่น คุณสามารถใช้การเชื่อมต่อเพื่อทำงานเหล่านี้ได้:

* สร้างรายการ SharePoint
* รับข้อมูลจากไฟล์ Excel ในบัญชีผู้ใช้ OneDrive for Business หรือ Dropbox ของคุณ
* ส่งอีเมลใน Office 365
* โพสต์ทวีต

คุณสามารถสร้างการเชื่อมต่อในหลายสถานการณ์เช่นดังต่อไปนี้ได้:

* การสร้าง[โฟลว์จากเทมเพลต](get-started-logic-template.md)
* สร้างการ[โฟลว์จากเอกสารเปล่า](get-started-logic-flow.md)หรือการปรับปรุงมีโฟลว์ที่มีอยู่
* สร้างการเชื่อมต่อในการ[เว็บไซต์ Microsoft Flow] [ 1]โดยตรง

หัวข้อนี้แสดงวิธีจัดการการเชื่อมต่อใน[เว็บไซต์ Microsoft Flow][1]

## <a name="add-a-connection"></a>เพิ่มการเชื่อมต่อ
1. ใน[เว็บไซต์ Microsoft Flow][1] ลงชื่อเข้าใช้ด้วยบัญชีที่ทำงานหรือองค์กรของคุณ
2. ใกล้กับมุมขวาบน เลือกไอคอนรูปเฟือง จากนั้นเลือก**การเชื่อมต่อ**
   
    ![เลือกการเชื่อมต่อ](./media/add-manage-connections/connections-menu.png)
3. เลือก **สร้างการเชื่อมต่อ**
4. ในรายการของ**การเชื่อมต่อที่พร้อมใช้งาน** เลือกการเชื่อมต่อที่คุณต้องการตั้งค่า เช่น SharePoint
5. เลือกปุ่ม**สร้างการเชื่อมต่อ** จากนั้นใส่ข้อมูลประจำตัวของคุณเพื่อตั้งค่าการเชื่อมต่อดังกล่าว

เมื่อตั้งค่าการเชื่อมต่อแล้ว การเชื่อมต่อดังกล่าวจะแสดงอยู่ในรายการ**การเชื่อมต่อของฉัน**

## <a name="connect-to-your-data-through-an-on-premises-data-gateway"></a>เชื่อมต่อกับข้อมูลของคุณผ่านการเกตเวย์ข้อมูลภายในองค์กร
สำหรับการเขียนนี้ SQL Server และ SharePoint Server สนับสนุนเกตเวย์ข้อมูลภายในองค์กร เมื่อต้องสร้างการเชื่อมต่อที่ใช้เกตเวย์:

1. ให้ทำตามขั้นตอนก่อนหน้าในหัวข้อนี้เพื่อเพิ่มการเชื่อมต่อ
2. ในรายการของ**เชื่อมต่อที่พร้อมใช้งาน** เลือก**SQL Server** จากนั้นเลือกกล่องกาเครื่องหมาย**เชื่อมต่อผ่านเกตเวย์ข้อมูลภายในองค์กร**
   
    ![เลือกเกตเวย์](./media/add-manage-connections/select-gateway.png)
   
   > [!IMPORTANT]
   > เกตเวย์ข้อมูล Microsoft SharePoint สนับสนุนปริมาณการใช้งาน HTTP แต่ไม่สนับสนุนปริมาณการใช้งาน HTTPS
   > 
   > 
3. ระบุข้อมูลประจำตัวของการเชื่อมต่อ จากนั้น เลือกเกตเวย์ที่คุณต้องการใช้
   
    สำหรับข้อมูลเพิ่มเติม ดู[จัดการเกตเวย์](gateway-manage.md)และ[ทำความเข้าใจเกตเวย์](gateway-reference.md)
   
    เมื่อตั้งค่าการเชื่อมต่อแล้ว การเชื่อมต่อดังกล่าวจะแสดงอยู่ในรายการ**การเชื่อมต่อของฉัน**

## <a name="delete-a-connection"></a>ลบการเชื่อมต่อ
1. ไปยังหน้า**เชื่อมต่อของฉัน** จากนั้นเลือกไอคอนถังขยะสำหรับการเชื่อมต่อที่คุณต้องการลบ
   
    ![ลบการเชื่อมต่อ](./media/add-manage-connections/delete-connection.png)
2. เลือก**ตกลง**เพื่อยืนยันว่าคุณต้องการลบการเชื่อมต่อ
   
    ![ยืนยันการลบ](./media/add-manage-connections/delete-confirmation.png)

เมื่อคุณลบการเชื่อมต่อ การเชื่อมต่อนั้นจะถูกลบออกจากทั้ง PowerApps และ Microsoft Flow

## <a name="update-a-connection"></a>อัปเดตการเชื่อมต่อ
คุณสามารถอัปเดตการเชื่อมต่อที่ไม่ทำงานเนื่องจากรายละเอียดบัญชีของคุณหรือรหัสผ่านของคุณเปลี่ยนแปลงได้

1. บนหน้า**การเชื่อมต่อของฉัน** เลือกลิงก์**ตรวจสอบรหัสผ่าน**สำหรับการเชื่อมต่อที่คุณต้องการอัปเดต
   
    ![ยืนยันรหัสผ่าน](./media/add-manage-connections/verify-password.png)
2. เมื่อได้รับข้อความปรากฏ ให้อัปเดตการเชื่อมต่อของคุณด้วยข้อมูลประจำตัวใหม่

เมื่อคุณอัปเดตการเชื่อมต่อ การเชื่อมต่อจะได้รับการอัปเดตสำหรับทั้ง PowerApps และ Microsoft Flow

## <a name="troubleshoot-a-connection"></a>การแก้ไขปัญหาการเชื่อมต่อ
คุณอาจจำเป็นต้องใช้บัญชีเดียวกันสำหรับการลงชื่อเข้าใช้ Microsoft Flow และสร้างการเชื่อมต่อกับ SharePoint, Office 365 หรือ OneDrive for Business ทั้งนี้ขึ้นอยู่กับนโยบายขององค์กรของคุณ

ตัวอย่างเช่น คุณอาจลงชื่อเข้าใช้ Microsoft Flow ด้วย *yourname@outlook.com* แต่ถูกบล็อกเมื่อคุณพยายามเชื่อมต่อกับ SharePoint ด้วย  *yourname@contoso.com* ได้ แต่คุณสามารถลงชื่อเข้าใช้ Microsoft Flow ด้วย *yourname@contoso.com* ได้ และคุณจะสามารถเชื่อมต่อไปยัง SharePoint ได้

<!--Reference links in article-->
[1]: https://flow.microsoft.com
