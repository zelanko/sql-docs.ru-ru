---
title: Требуемые параметры клиента | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory handler in RDS [ADO]
ms.assetid: e776b4e3-fcc4-4bfb-a7e8-5ffae1d83833
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bdb99cb3d792900f48ceb69c25c7ae720c339683
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67922296"
---
# <a name="required-client-settings"></a>Требуемые параметры клиента
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Чтобы использовать пользовательский обработчик **фактов** , укажите следующие параметры.  
  
-   Укажите "Provider = MS Remote" [в свойстве](../../../ado/reference/ado-api/provider-property-ado.md) [объекта соединения (](../../../ado/reference/ado-api/connection-object-ado.md) ADO) или в строке подключения объекта **соединения** "**provider**=".  
  
-   Задайте для свойства [CursorLocation (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md) значение **адусеклиент**.  
  
-   Укажите имя обработчика для использования в свойстве **обработчика** объекта данных [(RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md) или в строке соединения объекта [Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) для строки подключения "**handler**=". (Нельзя задать обработчик в строке соединения объекта **соединения** .)  
  
 RDS предоставляет обработчик по умолчанию на сервере с именем **мсдфмап. Обработчик**. (Файл настройки по умолчанию называется МСДФМАП. INI.)  
  
 **Пример**  
  
 Предположим, что следующие разделы в **мсдфмап. INI** и имя источника данных адвворкс были ранее определены:  
  
```console
[connect CustomerDataBase]  
Access=ReadWrite  
Connect="DSN=AdvWorks"  
  
[sql CustomerById]  
SQL="SELECT * FROM Customers WHERE CustomerID = ?"  
```  
  
 Следующие фрагменты кода написаны на Visual Basic:  
  
## <a name="rdsdatacontrol-version"></a>Клиент. Версия элемента управления  
  
```vb
Dim dc as New RDS.DataControl  
Set dc.Handler = "MSDFMAP.Handler"  
Set dc.Server = "https://yourServer"  
Set dc.Connect = "Data Source=CustomerDatabase"  
Set dc.SQL = "CustomerById(4)"  
dc.Refresh  
```  
  
## <a name="recordset-version"></a>Версия набора записей  
  
```vb
Dim rs as New ADODB.Recordset  
rs.CursorLocation = adUseClient  
```  
  
 Укажите свойство [обработчика (RDS)](../../../ado/reference/rds-api/handler-property-rds.md) или ключевое слово. Свойство [поставщика (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) или ключевое слово; и идентификаторы *кустомербид* и *кустомердатабасе* . Затем откройте объект **Recordset**  
  
 стандарт. Откройте "Кустомербид (4)", "handler = МСДФМАП. Обработчик; "& _  
  
```vb
"Provider=MS Remote;Data Source=CustomerDatabase;" & _  
"Remote Server=https://yourServer"  
```  
  
## <a name="see-also"></a>См. также:  
 [Раздел "Подключение файла настройки"](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Раздел файла настройки SQL](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Раздел UserList файла настройки](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Настройка в отношении фактов](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Требуемые параметры клиента](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Общие сведения о файле настройки](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Создание собственного настраиваемого обработчика](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)

