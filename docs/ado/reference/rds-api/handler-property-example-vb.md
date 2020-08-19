---
description: Пример свойства Handler (Visual Basic)
title: Пример свойства Handler (Visual Basic) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Handler property [ADO], Visual Basic example
ms.assetid: 9664f9a6-65fc-4e7f-be3d-3e4b501b558a
author: rothja
ms.author: jroth
ms.openlocfilehash: d00626b04c4107ffdbf15cd24b104b17602fc6e3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438976"
---
# <a name="handler-property-example-vb"></a>Пример свойства Handler (Visual Basic)
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 В этом примере демонстрируется свойство [обработчика](../../../ado/reference/rds-api/handler-property-rds.md) объектов [RDS элемента управления](../../../ado/reference/rds-api/datacontrol-object-rds.md) . (Дополнительные сведения см. в разделе [Настройка фактов](../../../ado/guide/remote-data-service/datafactory-customization.md) .)  
  
 Предположим, что следующие разделы в файле параметров, Msdfmap.ini, расположены на сервере:  
  
```  
[connect AuthorDataBase]  
Access=ReadWrite  
Connect="DSN=Pubs"  
[sql AuthorById]  
SQL="SELECT * FROM Authors WHERE au_id = ?"  
```  
  
 Код выглядит следующим образом. Команда, назначенная свойству [SQL](../../../ado/reference/rds-api/sql-property.md) , будет соответствовать идентификатору ***аусорбид*** и будет получать строку для автора Ивана о'леари. Свойство **Recordset** объекта **элемента управления** данных назначается несвязанному объекту [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) исключительно в качестве удобства для написания кода.  
  
```  
'BeginHandlerVB  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    Dim dc As New DataControl  
    Dim rst As ADODB.Recordset  
  
    dc.Handler = "MSDFMAP.Handler"  
    dc.ExecuteOptions = 1  
    dc.FetchOptions = 1  
    dc.Server = "https://MyServer"  
    dc.Connect = "Data Source=AuthorDataBase"  
    dc.SQL = "AuthorById('267-41-2394')"  
    dc.Refresh                  'Retrieve the record  
    Set rst = dc.Recordset      'Use another Recordset as a convenience  
    Debug.Print "Author is '" & rst!au_fname & " " & rst!au_lname & "'"  
  
    ' clean up  
    If rst.State = adStateOpen Then rst.Close  
    Set rst = Nothing  
    Set dc = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rst Is Nothing Then  
        If rst.State = adStateOpen Then rst.Close  
    End If  
    Set rst = Nothing  
    Set dc = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndHandlerVB  
```  
  
## <a name="see-also"></a>См. также:  
 [Объект элемента управления (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [Свойство Handler (служба удаленных рабочих столов)](../../../ado/reference/rds-api/handler-property-rds.md)


