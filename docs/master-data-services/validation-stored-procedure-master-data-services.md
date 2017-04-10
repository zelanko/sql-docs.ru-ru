---
title: "Проверка хранимых процедур (службы Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 332d3c86-4440-4f12-a6cb-ffbfbccde52c
caps.latest.revision: 8
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 8
---
# Проверка хранимых процедур (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]проверьте версию на применение бизнес-правил ко всем элементам версии модели.  
  
 В этом разделе объясняется, как использовать хранимую процедуру **mdm.udpValidateModel** для проверки данных. Администратор веб-приложения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] может проводить проверку в пользовательском интерфейсе. Дополнительные сведения см. в разделе [Подтверждение исправления проблемы, обнаруженной при проверке на соответствие бизнес-правилам (службы Master Data Services)](../master-data-services/validate-a-version-against-business-rules-master-data-services.md).  
  
> [!NOTE]  
>  При запуске проверки до завершения промежуточного процесса элементы, для которых этот процесс не был завершен, не будут проверены.  
  
## Пример  
  
```  
DECLARE @ModelName nVarchar(50) = 'Customer'   
DECLARE @Model_id int   
DECLARE @UserName nvarchar(50)= 'DOMAIN\user_name'   
DECLARE @User_ID int   
DECLARE @Version_ID int   
  
SET @User_ID = (SELECT ID    
                 FROM mdm.tblUser u   
                 WHERE u.UserName = @UserName)   
SET @Model_ID = (SELECT Top 1 Model_ID   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_Name = @ModelName)   
SET @Version_ID = (SELECT MAX(ID)   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_ID = @Model_ID)  
  
EXECUTE mdm.udpValidateModel @User_ID, @Model_ID, @Version_ID, 1  
  
```  
  
## Параметры  
 Параметры данной процедуры имеют следующие значения:  
  
|Параметр|Description|  
|---------------|-----------------|  
|UserID|Идентификатор пользователя.|  
|Model_ID|Идентификатор модели.|  
|Version_ID|Идентификатор версии.|  
  
## См. также:  
 [Обзор: импорт данных из таблиц (службы Master Data Services)](../master-data-services/overview-importing-data-from-tables-master-data-services.md)   
 [Подтверждение исправления проблемы, обнаруженной при проверке на соответствие бизнес-правилам (службы Master Data Services)](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
  