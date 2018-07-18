---
title: Обязательные параметры клиента | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory handler in RDS [ADO]
ms.assetid: e776b4e3-fcc4-4bfb-a7e8-5ffae1d83833
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d24dd3875d921020634ed418b9a7eed5b97178c
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35274293"
---
# <a name="required-client-settings"></a>Параметры клиента
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Укажите следующие параметры для использования пользовательского **DataFactory** обработчика.  
  
-   Укажите «поставщика = удаленное MS» в [объект соединения (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) объекта [свойства поставщика (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) свойство или **подключения** объекта строки подключения "**Поставщика**=» ключевое слово.  
  
-   Задать [CursorLocation свойство (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойства **adUseClient**.  
  
-   Укажите имя обработчика, используемого в [DataControl объекта (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта **обработчик** свойства, или [объекта набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) строка подключения объекта» **Обработчик**=» ключевое слово. (Невозможно задать обработчик в **подключения** строка подключения объекта.)  
  
 Служб удаленных рабочих СТОЛОВ предоставляет обработчик по умолчанию на сервере с именем **MSDFMAP. Обработчик**. (Файл настроек по умолчанию называется MSDFMAP. INI).  
  
 **Пример**  
  
 Предположим, что в следующих разделах в **MSDFMAP. INI** и имя источника данных, AdvWorks, ранее были определены:  
  
```  
[connect CustomerDataBase]  
Access=ReadWrite  
Connect="DSN=AdvWorks"  
  
[sql CustomerById]  
SQL="SELECT * FROM Customers WHERE CustomerID = ?"  
```  
  
 В следующих фрагментах кода на языке Visual Basic:  
  
## <a name="rdsdatacontrol-version"></a>RDS. Версия DataControl  
  
```  
Dim dc as New RDS.DataControl  
Set dc.Handler = "MSDFMAP.Handler"  
Set dc.Server = "http://yourServer"  
Set dc.Connect = "Data Source=CustomerDatabase"  
Set dc.SQL = "CustomerById(4)"  
dc.Refresh  
```  
  
## <a name="recordset-version"></a>Версия набора записей  
  
```  
Dim rs as New ADODB.Recordset  
rs.CursorLocation = adUseClient  
```  
  
 Укажите либо [свойства обработчика (RDS)](../../../ado/reference/rds-api/handler-property-rds.md) свойства или ключевым словом; [свойства поставщика (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) свойства или ключевого слова; и *CustomerById* и  *CustomerDatabase* идентификаторы. Затем откройте **записей** объекта  
  
 службы Reporting Services. Откройте «CustomerById(4)», «обработчик = MSDFMAP. Обработчик;» & _  
  
```  
"Provider=MS Remote;Data Source=CustomerDatabase;" & _  
"Remote Server=http://yourServer"  
```  
  
## <a name="see-also"></a>См. также  
 [Файл настроек присоединения раздела](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Раздел SQL настройки файла](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Раздел UserList настройки файла](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Настройка DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Параметры клиента](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Основные сведения о настройке файла](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Запись собственного настраиваемого обработчика](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)






















