---
title: "Файл настроек присоединения раздела | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connect section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: d50eb3cc-a822-486f-b80b-65bb50547ecd
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fe0012f287536d015e1086d02833a0f6651194f3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="customization-file-connect-section"></a>Файл настроек присоединения раздела
По умолчанию обработчик выполняется для запрета всех подключений. **Подключения** раздел задает исключения для этого поведения. Например, если все **подключения** разделы были отсутствует или пуст, то по умолчанию не может выполнять соединение.  
  
 **Подключения** раздел может содержать:  
  
-   Запись доступа по умолчанию, которая определяет значение по умолчанию операций чтения и записи на этом компьютере. Если отсутствует запись доступа по умолчанию в разделе, раздел будет пропущен.  
  
-   Новая строка подключения, заменяет строку подключения клиента.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
 Запись доступа по умолчанию имеет следующую форму:  
  
```  
  
Access=  
accessRight  
  
```  
  
 Запись строки замены соединения имеет следующую форму:  
  
```  
  
Connect=  
connectionString  
  
```  
  
## <a name="remarks"></a>Замечания  
  
|Часть|Description|  
|----------|-----------------|  
|**Соединить**|Строковый литерал, который указывает на это является запись строки соединения.|  
|***connectionString***|Строка, которая заменяет всю клиентскую строку подключения.|  
|**Доступ**|Строковый литерал, который указывает на это — это запись доступа.|  
|***accessRight***|Одно из следующих прав:<br /><br /> -   **NoAccess** — пользователь не может получить доступ к источнику данных.<br />-   **Только для чтения** — пользователь может просматривать источника данных.<br />-   **ReadWrite** — пользователь может считывать или запись в источнике данных.|  
  
 Если вы хотите разрешить любые соединения (в результате отключения обработчика поведения по умолчанию), задать запись доступом в **подключения по умолчанию** раздел `Access=ReadWrite`и удалите или закомментируйте любой другой **подключения** *идентификатор* раздела.  
  
## <a name="see-also"></a>См. также:  
 [Раздел журналы настройки файла](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Раздел SQL настройки файла](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Раздел UserList настройки файла](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Настройка DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Параметры клиента](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Основные сведения о настройке файла](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Запись собственного настраиваемого обработчика](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)



