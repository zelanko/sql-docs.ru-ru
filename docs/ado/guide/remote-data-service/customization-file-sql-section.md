---
title: Настройка раздела SQL файла | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ba0d8c7ab1294400c19456abf164c6ad6be0dd2e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704309"
---
# <a name="customization-file-sql-section"></a>Настройка раздела SQL файла
**Sql** раздел может содержать строку SQL, заменяет строку команды клиента. Если строка не SQL в разделе, раздел будет игнорироваться.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Новая строка SQL может быть *параметризованные*. То есть параметры, в **sql** разделе SQL-строку (обозначенный "?" символ) может быть заменена соответствующих аргументов в *идентификатор* в командной строке клиента (обозначенный Разделенный запятыми список в круглых скобках). Идентификатор и список аргументов ведут себя как вызов функции.  
  
 Предположим, например, строка команды клиента является `"CustomerByID(4)"`, заголовок раздела SQL `[SQL CustomerByID]`, и новый раздел SQL-строка представляет `"SELECT * FROM Customers WHERE CustomerID = ?".` создаст обработчик `"SELECT * FROM Customers WHERE CustomerID = 4"` и использовать эту строку для запросов к источнику данных.  
  
 Если новой инструкции SQL является пустая строка ("»), а затем в разделе учитывается.  
  
 Если новая строка инструкции SQL не является допустимым, то выполнение инструкции завершится ошибкой. Параметр клиента, фактически учитывается. Это можно сделать намеренно, чтобы «отключение» всех команд SQL клиента, указав:  
  
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
|**SQL**|Строковый литерал, указывающий, — это запись раздела SQL.|  
|***sqlString***|Строка SQL, который заменяет строку клиента.|  
  
## <a name="see-also"></a>См. также  
 [Настройка раздела подключения файла](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Настройка раздела журналов файла](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Настройка раздела UserList файла](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Настройка DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Необходимые параметры клиентов](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Общие сведения о файле настройки](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Запись собственного настраиваемого обработчика](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


