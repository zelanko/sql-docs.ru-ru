---
title: Свойство ActiveConnection (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::ActiveConnection
- Recordset15::get_ActiveConnection
- _Record::ActiveConnection
helpviewer_keywords:
- ActiveConnection property [ADO]
ms.assetid: 52d0a96c-14fb-4ad9-b004-4d821bc0a6db
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8dabf974e36b1f6beaff36f3a4888c128d7dfe1b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67921513"
---
# <a name="activeconnection-property-ado"></a>Свойство ActiveConnection (ADO)
Указывает, к какому объекту [соединения](../../../ado/reference/ado-api/connection-object-ado.md) в данный момент принадлежит указанная [команда](../../../ado/reference/ado-api/command-object-ado.md), [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md)или объект [записи](../../../ado/reference/ado-api/record-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает **строковое** значение, содержащее определение соединения, если соединение закрыто, или **вариант** , содержащий текущий объект **соединения** , если соединение открыто. По умолчанию используется пустая ссылка на объект. См. свойство [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) .  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **ActiveConnection** , чтобы определить объект **соединения** , для которого будет выполняться указанный объект **команды** , или будет открыт указанный **набор записей** .  
  
## <a name="command"></a>Get-Help  
 Для объектов **Command** свойство **ActiveConnection** доступно для чтения и записи.  
  
 При попытке вызвать метод [EXECUTE](../../../ado/reference/ado-api/execute-method-ado-command.md) для объекта **Command** перед установкой этого свойства в открытый объект **соединения** или допустимую строку подключения возникнет ошибка.  
  
 Если объект **соединения** назначен свойству **ActiveConnection** , то объект должен быть открыт. При назначении закрытого объекта соединения возникает ошибка.  
  
### <a name="note"></a>Примечание  
 **Microsoft Visual Basic** Если задать для свойства **ActiveConnection** значение Nothing, объект **команды** *не* будет связан с текущим **соединением** и будет вызван тем, что поставщик выпустит все связанные ресурсы в источнике данных. Затем можно связать объект **команды** с тем же или с другим объектом **Connection** . Некоторые поставщики позволяют изменить значение свойства с одного **соединения** на другое без необходимости присвоить свойству значение *Nothing*.  
  
 Если коллекция [Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md) объекта **Command** содержит параметры, предоставленные поставщиком, коллекция удаляется, если для свойства **ActiveConnection** задано значение *Nothing* или другой объект **соединения** . Если вы вручную создаете объекты [параметров](../../../ado/reference/ado-api/parameter-object.md) и используете их для заполнения коллекции **Parameters** объекта **Command** , установка свойства **ActiveConnection** в значение *Nothing* или на другой объект **соединения** оставляет коллекцию **параметров** неизменной.  
  
 При закрытии объекта **соединения** , с которым связан объект **команды** , свойству **ActiveConnection** присваивается значение *Nothing*. При присвоении этому свойству закрытого объекта **соединения** выдается ошибка.  
  
## <a name="recordset"></a>набор записей  
 Для открытых **объектов Recordset** или для объектов **набора записей** , свойству [Source](../../../ado/reference/ado-api/source-property-ado-recordset.md) которых задан допустимый объект **Command** , свойство **ActiveConnection** доступно только для чтения. В противном случае он доступен для чтения и записи.  
  
 Этому свойству можно присвоить допустимый объект **соединения** или допустимую строку подключения. В этом случае поставщик создает новый объект **соединения** с помощью этого определения и открывает соединение. Кроме того, поставщик может задать этому свойству новый объект **соединения** , чтобы предоставить возможность доступа к объекту **соединения** для получения расширенных сведений об ошибках или выполнения других команд.  
  
 При использовании аргумента *ActiveConnection* метода [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) для открытия объекта **Recordset** свойство **ActiveConnection** будет наследовать значение аргумента.  
  
 Если свойству **Source** объекта **Recordset** присвоено значение допустимой переменной объекта **Command** , свойство **ActiveConnection** **набора записей** наследует значение свойства **ActiveConnection** объекта **Command** .  
  
> [!NOTE]
>  **Использование удаленной службы данных** При использовании объекта **набора записей** на стороне клиента это свойство может быть установлено только в строку подключения или (в Microsoft Visual Basic или Visual Basic, Scripting Edition) в значение *Nothing*.  
  
## <a name="record"></a>Записей  
 Это свойство доступно для чтения и записи при закрытии объекта **Record** и может содержать строку соединения или ссылку на открытый объект **соединения** . Это свойство доступно только для чтения, если объект **Record** открыт, и содержит ссылку на открытый объект **соединения** .  
  
 Объект **соединения** создается неявно при открытии объекта **Record** из URL-адреса. Откройте **запись** с существующим открытым объектом **соединения** , назначив этому свойству объект **соединения** или используя объект **соединения** в качестве параметра в вызове метода [Open](../../../ado/reference/ado-api/open-method-ado-record.md) . Если **запись** была открыта из существующей **записи** или [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md), то она автоматически связывается с объектом **соединения** **записи** или объекта **набора записей** .  
  
> [!NOTE]
>  URL-адреса, использующие схему HTTP, автоматически вызывают [поставщик OLE DB Майкрософт для публикации в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Применяется к  
  
||||  
|-|-|-|  
|[Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>См. также:  
 [Пример свойств ActiveConnection, CommandText, CommandTimeout, CommandType, Size и Direction (Visual Basic)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [Пример свойств ActiveConnection, CommandText, CommandTimeout, CommandType, Size и Direction (Visual c++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [Пример свойств ActiveConnection, CommandText, CommandTimeout, CommandType, Size и Direction (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Свойство ConnectionString (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md)
