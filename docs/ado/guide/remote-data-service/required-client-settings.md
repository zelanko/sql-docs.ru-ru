---
title: Обязательные параметры клиента | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: cec3e79e3d37f064cb742588519a374737e01319
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558221"
---
# <a name="required-client-settings"></a>Требуемые параметры клиента
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Укажите следующие параметры для использования настраиваемой **DataFactory** обработчика.  
  
-   Укажите «поставщик = удаленное MS» в [объект соединения (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) объект [свойство Provider (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) свойство или **подключения** объекта строки подключения "**Поставщика**=» ключевое слово.  
  
-   Задайте [свойство CursorLocation (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойства **adUseClient**.  
  
-   Укажите имя обработчика, используемого в [объекта DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта **обработчик** свойство, или [объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) строки подключения объекта« **Обработчик**=» ключевое слово. (Нельзя установить в обработчике **подключения** строка подключения объекта.)  
  
 RDS предоставляет обработчик по умолчанию на сервере с именем **MSDFMAP. Обработчик**. (Файл настройки по умолчанию называется MSDFMAP. INI).  
  
 **Пример**  
  
 Предположим, что в следующих разделах в **MSDFMAP. INI** и имя источника данных, AdvWorks, ранее были определены:  
  
```console
[connect CustomerDataBase]  
Access=ReadWrite  
Connect="DSN=AdvWorks"  
  
[sql CustomerById]  
SQL="SELECT * FROM Customers WHERE CustomerID = ?"  
```  
  
 В следующих фрагментах кода создаются на языке Visual Basic:  
  
## <a name="rdsdatacontrol-version"></a>RDS. Версия DataControl  
  
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
  
 Укажите либо [свойство обработчика (RDS)](../../../ado/reference/rds-api/handler-property-rds.md) свойство или ключевое слово; [свойство Provider (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) свойство или ключевое слово; и *CustomerById* и  *CustomerDatabase* идентификаторы. Затем откройте **записей** объекта  
  
 RS. Откройте «CustomerById(4)», «обработчик = MSDFMAP. Обработчик»; "и" _  
  
```vb
"Provider=MS Remote;Data Source=CustomerDatabase;" & _  
"Remote Server=https://yourServer"  
```  
  
## <a name="see-also"></a>См. также  
 [Настройка раздела подключения файла](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Настройка раздела SQL файла](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Настройка раздела UserList файла](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Настройка DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Необходимые параметры клиентов](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Общие сведения о файле настройки](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Запись собственного настраиваемого обработчика](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)

