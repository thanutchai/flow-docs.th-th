---
title: ขีดจำกัดและการกำหนดค่า | Microsoft Docs
description: ขีดจำกัดและการกำหนดค่า
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
ms.date: 06/19/2018
ms.author: stepsic
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 1d4585d18b83975ba888a7685e8556c778889ee1
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: th-TH
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690594"
---
# <a name="limits-and-configuration-in-microsoft-flow"></a>ขีดจำกัดและการกำหนดค่าใน Microsoft Flow
หัวข้อนี้ประกอบด้วยข้อมูลเกี่ยวกับข้อจำกัดปัจจุบันและรายละเอียดการกำหนดค่าสำหรับโฟลว์

## <a name="request-limits"></a>ขีดจำกัดคำขอ
ต่อไปนี้คือขีดจำกัดสำหรับคำขอขาออกเดียว

### <a name="timeout"></a>หมดเวลา

| ชื่อ | ขีดจำกัด |
| --- | --- |
| คำขอหมดเวลาสำหรับการเรียกใช้แบบซิงโครนัส |120 วินาที |
| คำขอหมดเวลาสำหรับการเรียกใช้ต่างเวลา|สามารถกำหนดค่าได้ สูงสุดคือ 30 วัน |

### <a name="message-size"></a>ขนาดของข้อความ

| ชื่อ | ขีดจำกัด | บันทึกย่อ |
| --- | --- | --- |
| ขนาดของข้อความ |100 MB |ไม่ใช่ทุก API ที่สนับสนุน 100MB แบบเต็ม |
| ขีดจำกัดการประเมินนิพจน์ |131,072 อักขระ |`@concat()`, `@base64()`,`string` ต้องไม่เกินขีดจำกัดนี้ได้ |

### <a name="retry-policy"></a>นโยบายการทำซ้ำ

| ชื่อ | ขีดจำกัด |
| --- | --- |
| ความพยายามอีกครั้ง |90 | ค่าเริ่มต้นคือ 4 หากต้องการเปลี่ยนการตั้งค่าการใช้งานเริ่มต้น | 
| ลองการหน่วงเวลาสูงสุดอีกครั้ง |1 วัน | |
| ลองการหน่วงเวลาต่ำสุดอีกครั้ง |5 วินาที | |

## <a name="run-duration-and-retention"></a>ระยะเวลาการเรียกใช้และการเก็บข้อมูล
ต่อไปนี้คือขีดจำกัดสำหรับการใช้งานโฟลว์ครั้งเดียว

| ชื่อ | ขีดจำกัด | บันทึกย่อ |
| --- | --- | --- |
| ระยะเวลาการเรียกใช้ |30 วัน |รวมเวิร์กโฟลว์ที่มีขั้นตอนระหว่างรอ เช่น การอนุมัติ หลังจาก 30 วัน ขั้นตอนระหว่างรอใด ๆ จะหมดเวลา การอนุมัติที่หมดเวลาจะถูกลบออกจากศูนย์การอนุมัติ หากมีใครบางคนพยายามที่จะอนุมัติคำขอที่หมดเวลา ผู้ใช้ดังกล่าวจะได้รับข้อความข้อผิดพลาด |
| การจัดเก็บข้อมูล |30 วัน |ซึ่งนับจากเวลาเริ่มต้นใช้งาน |
| ช่วงการเกิดซ้ำค่าต่ำสุด |1 นาที | |
| ช่วงการเกิดซ้ำค่าสูงสุด |500 วัน | |
| ประวัติการเก็บข้อมูลการเรียกใช้สูงสุด |28 วันต่อกฎ GDPR | |

## <a name="looping-and-debatching-limits"></a>ขีดจำกัดการวนรอบและการยกเลิกรวมกลุ่ม
เหล่านี้คือขีดจำกัดสำหรับการใช้งานโฟลว์ครั้งเดียว

| ชื่อ | ขีดจำกัด | บันทึกย่อ |
| --- | --- | --- |
| นำไปใช้ในแต่ละรายการ |100,000 |100,000 จะพร้อมใช้งานสำหรับแผนพรีเมียมเท่านั้น มิฉะนั้น คุณจะถูกจำกัดแค่ 5,000 คุณสามารถใช้การดำเนินการตัวกรองเพื่อกรองอาร์เรย์ที่ใหญ่กว่าตามความจำเป็นได้ |
| จนกว่าจะมีการวนซ้ำ |5,000 | |
| รายการ SplitOn |100,000 |เช่นเดียวกับการนำไปใช้กับแต่ละอัน ขีดจำกัดคือ 5,000 เว้นแต่คุณจะอยู่ในแผนพรีเมี่ยม |
| นำไปใช้กับโครงสร้างคู่ขนาน |50 |ตามค่าเริ่มต้น ลูปจะทำงานตามลําดับ (โดยนัยคือ โครงสร้างคู่ขนานเท่ากับ 1) คุณสามารถกำหนดค่าสูงสุด 50 ในแบบขนาน |
| ดำเนินการทำงานต่อ 5 นาที | 100,000 | นอกจากนี้ คุณยังสามารถแจกจ่ายปริมาณงานได้มากกว่าหนึ่งรูปแบบตามต้องการ |
| การดำเนินการโทรออกพร้อมกัน | ~2,500 | ลดจำนวนคำขอที่เกิดขึ้นพร้อมกันหรือลดระยะเวลาตามความต้องการ | 

## <a name="definition-limits"></a>ขีดจำกัดคำจำกัดความ
เหล่านี้คือขีดจำกัดสำหรับโฟลว์เดียว

| ชื่อ | ขีดจำกัด | บันทึกย่อ |
| --- | --- | --- |
| การดำเนินการต่อเวิร์กโฟลว์ |250 |คุณสามารถเพิ่มและซ้อนเวิร์กโฟลว์เพื่อขยายส่วนนี้ได้ตามความจำเป็น |
| ความลึกการซ้อนกันของการดำเนินการที่อนุญาต |5 |คุณสามารถเพิ่มและซ้อนเวิร์กโฟลว์เพื่อขยายส่วนนี้ได้ตามความจำเป็น |
| อักขระสูงสุดต่อนิพจน์ |8,192 | |
| `action`/`trigger` ขีดจำกัดชื่อ |80 | |
| `description` ขีดจำกัดความยาว |256 | |

## <a name="sharepoint-limits"></a>ขีดจำกัด SharePoint
มี[ข้อจำกัด](https://powerapps.microsoft.com/tutorials/connection-sharepoint-online/)ในวิธีการที่คุณสามารถใช้ Microsoft SharePoint กับ Microsoft Flow และ PowerApps

## <a name="ip-address-configuration"></a>การกำหนดค่าที่อยู่ IP
ที่อยู่ IP ที่ Microsoft Flow ส่งคำขอขึ้นอยู่กับ[ภูมิภาค](regions-overview.md)ที่มี[สภาพแวดล้อม](environments-overview-admin.md)ที่ประกอบด้วยโฟลว์นั้นอยู่ ในขณะนี้เราไม่เผยแพร่ FQDN ที่พร้อมใช้งานสำหรับสถานการณ์สมมติโฟลว์

### <a name="logic-app-service"></a>บริการ Logic App
การเรียกใช้จากโฟลว์จะผ่านบริการ Logic App ของ Azure โดยตรง ตัวอย่างบางส่วนของการเรียกใช้เหล่านี้รวมถึง HTTP หรือ HTTP + OpenAPI การเรียกใช้เหล่านี้มาจากที่อยู่ IP ต่อไปนี้:

| ภูมิภาค | IP ขาออก |
| --- | --- |
| เอเชีย |168.63.200.173, 13.75.89.159, 23.97.68.172, 13.75.94.173, 40.83.127.19, 52.175.33.254, 52.163.93.214, 52.187.65.81, 52.187.65.155, 13.76.133.155, 52.163.228.93, 52.163.230.166 |
| ออสเตรเลีย |13.75.153.66, 104.210.89.222, 104.210.89.244, 13.75.149.4, 104.210.91.55, 104.210.90.241, 13.73.115.153, 40.115.78.70, 40.115.78.237, 13.73.114.207, 13.77.3.139, 13.70.159.205 |
| แคนาดา |52.233.29.92, 52.228.39.241, 52.228.39.244, 52.232.128.155, 52.229.120.45, 52.229.126.25 |
| ยุโรป |13.79.173.49, 52.169.218.253, 52.169.220.174, 40.113.12.95, 52.178.165.215, 52.178.166.21, 13.95.155.53, 52.174.54.218, 52.174.49.6, 40.68.222.65, 40.68.209.23, 13.95.147.65 |
| อินเดีย |52.172.157.194, 52.172.184.192, 52.172.191.194, 52.172.154.168, 52.172.186.159, 52.172.185.79, 52.172.9.47, 52.172.49.43, 52.172.51.140, 52.172.50.24, 52.172.55.231, 52.172.52.0 |
| ญี่ปุ่น |13.71.146.140, 13.78.84.187, 13.78.62.130, 13.71.158.3, 13.73.4.207, 13.71.158.120, 40.74.140.173, 40.74.81.13, 40.74.85.215, 40.74.140.4, 104.214.137.243, 138.91.26.45 |
| สหรัฐอเมริกา |137.135.106.54, 40.117.99.79, 40.117.100.228, 13.92.98.111, 40.121.91.41, 40.114.82.191, 52.160.90.237, 138.91.188.137, 13.91.252.184, 52.160.92.112, 40.118.244.241, 40.118.241.243 |

### <a name="services"></a>บริการ

> [!IMPORTANT]
>   หากคุณมีการกำหนดค่าที่มีอยู่ โปรดอัปเดตโดยเร็วที่สุดก่อนวันที่ 1 กันยายน 2018 เพื่อให้รวมและตรงกับที่อยู่ IP ในรายการนี้สำหรับภูมิภาคที่โฟลว์ของคุณมีอยู่

การเรียกใช้จาก API ที่เชื่อมต่อผ่านโฟลว์หนึ่ง (ตัวอย่างเช่น SQL, API หรือ SharePoint API) จะมาจากที่อยู่ IP ที่ระบุไว้ด้านล่าง:

| ภูมิภาค | IP ขาออก |
| --- | --- |
| เอเชีย |13.75.36.64 - 13.75.36.79, 13.67.8.240 - 13.67.8.255, 52.175.23.169, 52.187.68.19, 52.163.91.227, 52.163.89.40, 52.163.89.65, 52.163.95.29, 52.187.53.78, 13.75.89.9, 13.75.91.198, 13.75.92.202, 13.75.92.124, 23.97.72.250 |
| ออสเตรเลีย |13.70.72.192 - 13.70.72.207, 13.72.243.10, 13.77.50.240 - 13.77.50.255, 13.70.136.174, 13.77.7.172, 13.70.191.49, 13.70.189.7, 13.70.187.251, 13.70.188.38, 13.70.82.210, 13.73.203.158, 13.73.207.42, 13.73.205.35, 13.70.88.23 |
| บราซิล |191.233.203.192 - 191.233.203.207, 104.214.19.48 - 104.214.19.63, 13.65.86.57, 104.41.59.51 |
| แคนาดา |13.71.170.208 - 13.71.170.223, 13.71.170.224 - 13.71.170.239, 52.237.24.126, 40.69.106.240 - 40.69.106.255, 52.242.35.152, 52.233.30.222, 52.233.30.148, 52.233.30.199, 52.233.29.254, 52.232.130.205, 52.229.126.118, 52.229.126.28, 52.229.123.56, 52.229.123.161, 52.233.27.68 |
| ยุโรป |13.69.227.208 - 13.69.227.223, 52.178.150.68, 13.69.64.208 - 13.69.64.223, 52.174.88.118, 52.166.241.149, 52.166.244.232, 52.166.245.173, 52.166.243.169, 52.178.37.42, 40.69.45.126, 40.69.45.11, 40.69.45.93, 40.69.42.254, 52.164.249.26, 137.117.161.181 |
| อินเดีย |104.211.81.192 - 104.211.81.207, 52.172.211.12, 40.78.194.240 - 40.78.194.255, 13.71.125.22, 104.211.146.224 - 104.211.146.239, 104.211.189.218, 52.172.54.172, 52.172.55.107, 52.172.55.84, 52.172.51.70, 52.172.49.180, 52.172.158.185, 52.172.159.100, 52.172.158.2, 52.172.155.245, 52.172.153.107 |
| ญี่ปุ่น |13.78.108.0 - 13.78.108.15, 13.71.153.19, 40.74.100.224 - 40.74.100.239, 104.215.61.248, 104.214.137.186, 104.214.139.29, 104.214.140.23, 104.214.138.174, 104.214.151.229, 13.78.85.193, 13.78.84.73, 13.78.85.200, 13.78.86.229, 13.78.121.151 |
| สหราชอาณาจักร |51.140.148.0 - 51.140.148.15, 51.140.80.51, 51.140.211.0 - 51.140.211.15, 51.141.47.105 |
| สหรัฐอเมริกา |13.89.171.80 - 13.89.171.95, 52.173.245.164, 40.71.11.80 - 40.71.11.95, 40.71.249.205, 40.70.146.208 - 40.70.146.223, 52.232.188.154, 52.162.107.160 - 52.162.107.175, 52.162.242.161, 40.112.243.160 - 40.112.243.175, 104.42.122.49, 104.43.232.28, 104.43.232.242, 104.43.235.249, 104.43.234.211, 40.78.144.221, 52.160.93.247, 52.160.91.66, 52.160.92.131, 52.160.95.100, 13.93.159.171, 40.117.101.91, 40.117.98.246, 40.117.101.120, 40.117.100.191, 23.96.11.216 |
| สหรัฐอเมริกา (การเข้าถึงก่อนใคร) |13.71.195.32 - 13.71.195.47, 52.161.102.22, 13.66.140.128 - 13.66.140.143, 52.183.78.157, 52.161.26.191, 52.161.27.42, 52.161.29.40, 52.161.26.33, 52.161.31.35, 13.66.213.240, 13.66.214.51, 13.66.210.166, 13.66.213.29, 13.66.208.24 |

ตัวอย่างเช่น ถ้าคุณต้องอนุญาตที่อยู่ IP สำหรับฐานข้อมูล Azure SQL ของคุณ คุณควรใช้ที่อยู่เหล่านี้

ตารางต่อไปนี้แสดงรายการบริการที่เชื่อมต่อกับ Microsoft Flow ตรวจสอบให้แน่ใจว่าไม่มีการบล็อกบริการเหล่านี้บนเครือข่ายของคุณ

โดเมน | โพรโทคอล | ใช้
--------|  ---------| -----
management.azure.com|https|เข้าใช้งานที่ Azure Resource Manager
login.microsoft.com</br>login.windows.net</br>login.microsoftonline.com</br>secure.aadcdn.microsoftonline-p.com|https|เข้าใช้งาน Active Directory Authentication Library (ADAL)
graph.microsoft.com </br>graph.windows.net</br>|https|เข้าใช้งาน Azure AD Graph API สำหรับการรับข้อมูลผู้ใช้เช่น รูปภาพโปรไฟล์
*.azure-apim.net|https|เข้าถึง รันไทม์ สำหรับตัวเชื่อมต่อ
*.flow.microsoft.com|https|เข้าถึงไปยังไซต์ Microsoft Flow
*.powerapps.com|https|การเข้าถึงไซต์ PowerApps
psux.azureedge.net|https|เข้าใช้งาน Microsoft Flow CDN
nps.onyx.azure.net|https|เข้าถึง NPS (Net Promoter Score)

