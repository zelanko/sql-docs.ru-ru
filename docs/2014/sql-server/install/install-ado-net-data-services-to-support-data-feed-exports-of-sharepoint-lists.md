---
title: Установка служб данных ADO.NET для поддержки данных веб-канала экспорта списков SharePoint | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f32527ae-f623-4e08-adfb-6d3262f5c2ac
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: d4241d56aa3257bd0ec2cddf4b439a4939f8ab9f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097834"
---
# <a name="install-adonet-data-services-to-support-data-feed-exports-of-sharepoint-lists"></a>Для поддержки экспорта списков SharePoint в виде веб-каналов данных установите службы ADO.NET Data Services
  Для обеспечения возможности экспорта списков SharePoint в виде веб-каналов данных требуется служба ADO.NET Data Services. SharePoint 2010 не включает этот компонент в установщик компонентов, необходимых для SharePoint 2010, поэтому его необходимо устанавливать вручную.  
  
 Без этих предварительных условий, возникнет следующая ошибка при попытке использования списка SharePoint, который был экспортирован в виде потока данных: «по соображениям безопасности DTD запрещен в этом документе XML. Для разрешения обработки DTD присвойте свойству ProhibitDtd в XmlReaderSettings значение false и передайте параметры в метод XmlReader.Create».  
  
 Используйте следующие инструкции для установки служб ADO.NET Data Services на каждом сервере SharePoint, для которого нужно разрешить экспорт списков как веб-каналов данных.  
  
### <a name="download-and-install-adonet-data-services"></a>Загрузка и установка служб ADO.NET Data Services  
  
1.  Перейдите в документации требования к оборудованию и программному обеспечению для SharePoint 2010 [оборудованию и программному обеспечению (SharePoint 2010)](http://go.microsoft.com/fwlink/?LinkId=169734)  
  
2.  В **доступ к применимым программам**, найдите ссылку на ADO.NET Data Services 3.5, соответствующую операционной системе (Windows Server 2008 SP2 или Windows Server 2008 R2).  
  
3.  Щелкните ссылку и запустите программу установки службы.  
  
## <a name="see-also"></a>См. также  
 [Установка PowerPivot для SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  