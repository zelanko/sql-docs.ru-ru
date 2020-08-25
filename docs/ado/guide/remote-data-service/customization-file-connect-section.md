---
description: Настройка раздела подключения файла
title: Раздел "Подключение файла настройки" | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connect section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: d50eb3cc-a822-486f-b80b-65bb50547ecd
author: rothja
ms.author: jroth
ms.openlocfilehash: a8c712efc368d9b84158697d3b7e6eedfb4224ff
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88759850"
---
# <a name="customization-file-connect-section"></a>Настройка раздела подключения файла
Поведение обработчика по умолчанию заключается в запрете всех подключений. В разделе **Connect** указываются исключения из этого поведения. Например, если все разделы **соединения** отсутствовали или пусты, то по умолчанию соединения устанавливаться не могут.  
  
 Раздел **Connect** может содержать:  
  
-   Запись доступа по умолчанию, которая указывает операции чтения и записи по умолчанию, разрешенные для этого соединения. Если в разделе нет записи доступа по умолчанию, раздел будет проигнорирован.  
  
-   Новая строка подключения, которая заменяет строку подключения клиента.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
 Запись доступа по умолчанию имеет вид:  
  
```console
  
Access=  
accessRight  
  
```  
  
 Заменяющая строка подключения имеет вид:  
  
```console
  
Connect=  
connectionString  
  
```  
  
## <a name="remarks"></a>Remarks  
  
|Часть|Описание|  
|----------|-----------------|  
|**Подключить**|Литеральная строка, указывающая, что это запись строки подключения.|  
|**_connectionString_**|Строка, которая заменяет всю строку подключения клиента.|  
|**Доступ**|Литеральная строка, указывающая, что это запись доступа.|  
|**_акцессригхт_**|Одно из следующих прав доступа:<br /><br /> -   Не **доступ** — пользователь не может получить доступ к источнику данных.<br />-   **Только для** чтения — пользователь может читать источник данных.<br />-   **ReadWrite** — пользователь может выполнять чтение или запись в источник данных.|  
  
 Если вы хотите разрешить любое подключение (в результате отключив поведение обработчика по умолчанию), задайте запись доступа в разделе **Connect Default** `Access=ReadWrite` , а затем удалите или закомментируйте любой другой раздел **Connect** _identifier_ .  
  
## <a name="see-also"></a>См. также  
 [Раздел журналов файлов настройки](./customization-file-logs-section.md)   
 [Раздел файла настройки SQL](./customization-file-sql-section.md)   
 [Раздел UserList файла настройки](./customization-file-userlist-section.md)   
 [Настройка в отношении фактов](./datafactory-customization.md)   
 [Требуемые параметры клиента](./required-client-settings.md)   
 [Общие сведения о файле настройки](./understanding-the-customization-file.md)   
 [Создание собственного настраиваемого обработчика](./writing-your-own-customized-handler.md)