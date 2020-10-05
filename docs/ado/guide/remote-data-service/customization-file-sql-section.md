---
description: Настройка раздела SQL файла
title: Раздел файла настройки SQL | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: e65c2871-9986-44ff-b8b7-7f5eda91b3fa
author: rothja
ms.author: jroth
ms.openlocfilehash: d17fa12aa0b07b265fb8f26b6ac1b6c584015d1e
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724765"
---
# <a name="customization-file-sql-section"></a>Настройка раздела SQL файла
Раздел **SQL** может содержать новую строку SQL, которая заменяет командную строку клиента. Если в разделе нет строки SQL, раздел будет проигнорирован.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](/dotnet/framework/wcf/).  
  
 Новая строка SQL может быть *параметризована*. Это значит, что параметры в строке SQL **строки SQL (** обозначенной символом "?") могут быть заменены соответствующими аргументами в *идентификаторе* в строке командной строки клиента (обозначенной с помощью списка с разделителями-запятыми в скобках). Идентификатор и список аргументов ведут себя как вызов функции.  
  
 Например, предположим, что Командная строка клиента — `"CustomerByID(4)"` , заголовок раздела SQL — `[SQL CustomerByID]` , а новая строка раздела SQL — `"SELECT * FROM Customers WHERE CustomerID = ?".` обработчик создает `"SELECT * FROM Customers WHERE CustomerID = 4"` и использует эту строку для запроса к источнику данных.  
  
 Если новая инструкция SQL является пустой строкой (""), раздел игнорируется.  
  
 Если новая строка инструкции SQL недопустима, выполнение инструкции завершится ошибкой. Параметр клиента фактически игнорируется. Это можно сделать намеренно, отключив все клиентские команды SQL, указав:  
  
```console
[SQL default]   
SQL = " "  
```  
  
## <a name="syntax"></a>Синтаксис  
 Запись строки SQL замены имеет вид:  
  
 **SQL =**   
 ***sqlString***  
  
|Часть|Описание|  
|----------|-----------------|  
|**SQL**|Литеральная строка, указывающая, что это запись раздела SQL.|  
|***sqlString***|Строка SQL, которая заменяет строку клиента.|  
  
## <a name="see-also"></a>См. также  
 [Раздел "Подключение файла настройки"](./customization-file-connect-section.md)   
 [Раздел журналов файлов настройки](./customization-file-logs-section.md)   
 [Раздел UserList файла настройки](./customization-file-userlist-section.md)   
 [Настройка в отношении фактов](./datafactory-customization.md)   
 [Требуемые параметры клиента](./required-client-settings.md)   
 [Общие сведения о файле настройки](./understanding-the-customization-file.md)   
 [Создание собственного настраиваемого обработчика](./writing-your-own-customized-handler.md)