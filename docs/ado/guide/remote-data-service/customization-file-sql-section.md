---
title: Раздел файла настройки SQL | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: 934b982004bf27e28a8daeed09061101886ce444
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82749879"
---
# <a name="customization-file-sql-section"></a>Настройка раздела SQL файла
Раздел **SQL** может содержать новую строку SQL, которая заменяет командную строку клиента. Если в разделе нет строки SQL, раздел будет проигнорирован.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
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
 [Раздел "Подключение файла настройки"](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Раздел журналов файлов настройки](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Раздел UserList файла настройки](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Настройка в отношении фактов](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Требуемые параметры клиента](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Общие сведения о файле настройки](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Создание собственного настраиваемого обработчика](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


