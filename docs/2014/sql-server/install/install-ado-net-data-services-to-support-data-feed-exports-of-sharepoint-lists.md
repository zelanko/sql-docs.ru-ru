---
title: Установка служб ADO.NET Data Services для поддержки экспорта каналов данных в списках SharePoint | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: f32527ae-f623-4e08-adfb-6d3262f5c2ac
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: b9b3ec2d8b7459f9d66313c6a40b1cbc26450e0d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "71952165"
---
# <a name="install-adonet-data-services-to-support-data-feed-exports-of-sharepoint-lists"></a>Для поддержки экспорта списков SharePoint в виде веб-каналов данных установите службы ADO.NET Data Services
  Для обеспечения возможности экспорта списков SharePoint в виде веб-каналов данных требуется служба ADO.NET Data Services. SharePoint 2010 не включает этот компонент в установщик компонентов, необходимых для SharePoint 2010, поэтому его необходимо устанавливать вручную.  
  
 Без этого предварительного требования при попытке использовать список SharePoint, экспортированный в виде потока данных, будет выдаваться следующая ошибка: "по соображениям безопасности DTD запрещен в этом XML-документе. Для разрешения обработки DTD присвойте свойству ProhibitDtd в XmlReaderSettings значение false и передайте параметры в метод XmlReader.Create».  
  
 Используйте следующие инструкции для установки служб ADO.NET Data Services на каждом сервере SharePoint, для которого нужно разрешить экспорт списков как веб-каналов данных.  
  
### <a name="download-and-install-adonet-data-services"></a>Загрузка и установка служб ADO.NET Data Services  
  
1.  Перейдите к документации по требованиям к оборудованию и программному обеспечению для SharePoint 2010, [требованиям к оборудованию и программному обеспечению (SharePoint 2010)](https://go.microsoft.com/fwlink/?LinkId=169734)  
  
2.  В окне **доступ к соответствующему программному обеспечению**найдите ссылку на ADO.NET Data Services 3,5, соответствующую используемой операционной системе (windows Server 2008 SP2 или windows Server 2008 R2).  
  
3.  Щелкните ссылку и запустите программу установки службы.  
  
## <a name="see-also"></a>См. также:  
 [Установка PowerPivot для SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
