---
title: Установка служб данных ADO.NET для поддержки данных экспорта списков SharePoint в виде веб-канала | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f32527ae-f623-4e08-adfb-6d3262f5c2ac
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 888e3bcf01f3cbb33ae11a3961a6d492040afb1f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187731"
---
# <a name="install-adonet-data-services-to-support-data-feed-exports-of-sharepoint-lists"></a>Для поддержки экспорта списков SharePoint в виде веб-каналов данных установите службы ADO.NET Data Services
  Для обеспечения возможности экспорта списков SharePoint в виде веб-каналов данных требуется служба ADO.NET Data Services. SharePoint 2010 не включает этот компонент в установщик компонентов, необходимых для SharePoint 2010, поэтому его необходимо устанавливать вручную.  
  
 Без этих предварительных условий, вы получите следующую ошибку при попытке использования списка SharePoint, который был экспортирован в виде канала данных: «по соображениям безопасности DTD запрещен в этом документе XML. Для разрешения обработки DTD присвойте свойству ProhibitDtd в XmlReaderSettings значение false и передайте параметры в метод XmlReader.Create».  
  
 Используйте следующие инструкции для установки служб ADO.NET Data Services на каждом сервере SharePoint, для которого нужно разрешить экспорт списков как веб-каналов данных.  
  
### <a name="download-and-install-adonet-data-services"></a>Загрузка и установка служб ADO.NET Data Services  
  
1.  Перейдите к документации требования к оборудованию и программному обеспечению для SharePoint 2010, [оборудованию и программному обеспечению (SharePoint 2010)](http://go.microsoft.com/fwlink/?LinkId=169734)  
  
2.  В **доступ к применимым программам**, найти ссылку на службы ADO.NET Data Services 3.5, соответствующую операционной системе, используемой (Windows Server 2008 SP2 или Windows Server 2008 R2).  
  
3.  Щелкните ссылку и запустите программу установки службы.  
  
## <a name="see-also"></a>См. также  
 [Установка PowerPivot для SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
