---
title: Раздел SQL файла настройки | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: e65c2871-9986-44ff-b8b7-7f5eda91b3fa
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6294ab601f527527cf69ca017e3643dfe98a1336
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="customization-file-sql-section"></a>Раздел SQL настройки файла
**Sql** раздел может содержать строку SQL, заменяющую строку команды клиента. Если строка не SQL в разделе, раздел будет пропущен.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Новая строка SQL могут быть *параметризованные*. То есть параметров в **sql** статьи строку SQL (обозначенный "?" символ) могут быть заменены соответствующими аргументами в *идентификатор* в командной строке клиента (обозначенный список с разделителями-запятыми в круглых скобках). Идентификатор и список аргументов ведут себя как вызов функции.  
  
 Предположим, например, строка команды клиента `"CustomerByID(4)"`, заголовок раздела SQL `[SQL CustomerByID]`, и новый раздел строка SQL представляет `"SELECT * FROM Customers WHERE CustomerID = ?".` создаст обработчик `"SELECT * FROM Customers WHERE CustomerID = 4"` и использовать эту строку для запросов к источнику данных.  
  
 Если инструкция SQL, новый, пустой строкой ("»), раздел игнорируется.  
  
 Если новая строка инструкции SQL не является допустимым, то выполнение инструкции завершится ошибкой. Параметр клиента эффективно игнорируется. Этого можно специально для «отключить» всех команд SQL для клиента, указав:  
  
```  
[SQL default]   
SQL = " "  
```  
  
## <a name="syntax"></a>Синтаксис  
 Замена записи строк SQL имеет следующую форму:  
  
 **SQL =**   
 ***sqlString***  
  
|Часть|Описание|  
|----------|-----------------|  
|**SQL**|Строковый литерал, который указывает на это — это запись раздел SQL.|  
|***sqlString***|Строка SQL, который заменяет строку клиента.|  
  
## <a name="see-also"></a>См. также  
 [Файл настроек присоединения раздела](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Раздел журналы настройки файла](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Раздел UserList настройки файла](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Настройка DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Параметры клиента](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Основные сведения о настройке файла](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Запись собственного настраиваемого обработчика](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


