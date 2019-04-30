---
title: Метод (объект Connection ADO) Open | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::raw_Open
- Connection15::Open
- _Connection::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: 663defab-5545-4973-9036-24d5882c9737
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 008ff3dacaa4bf3256429984973608c10a73d43e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63217670"
---
# <a name="open-method-ado-connection"></a>Метод Open (объект Connection ADO)
Открывает подключение к источнику данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
connection.Open ConnectionString, UserID, Password, Options  
```  
  
#### <a name="parameters"></a>Параметры  
 *connectionString*  
 Необязательный параметр. Объект **строка** значение, содержащее сведения о соединении. См. в разделе [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойство Дополнительные сведения о допустимых параметров.  
  
 *UserID*  
 Необязательный. Объект **строка** значение, содержащее имя пользователя для использования при установке соединения.  
  
 *Пароль*  
 Необязательный параметр. Объект **строка** значение, содержащее пароль для использования при установке соединения.  
  
 *Параметры*  
 Необязательный параметр. Объект [ConnectOptionEnum](../../../ado/reference/ado-api/connectoptionenum.md) значение, определяющее, является ли этот метод должен возвращать после (синхронно) или до (асинхронно) подключение будет установлено.  
  
## <a name="remarks"></a>Примечания  
 С помощью **откройте** метод [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объект устанавливает физическое соединение с источником данных. После успешного завершения этого метода, подключение считается активным, и можно выполнить команду в его и обрабатывать результаты.  
  
 Используйте необязательный *ConnectionString* аргумент для указания строки подключения, содержащий ряд *аргумент* *= value* инструкций, разделенных точкой с запятой, или файл или каталог ресурс, указанный в URL-адрес. **ConnectionString** свойство автоматически наследует значение, используемое для *ConnectionString* аргумент. Таким образом, то можно либо установить **ConnectionString** свойство **подключения** объекта перед его открытием, или использовать *ConnectionString* аргумент, чтобы задать или переопределить текущие параметры подключения во время **откройте** вызова метода.  
  
 При передаче имени пользователя и пароля сведений обоих в *ConnectionString* аргумент и в необязательном *UserID* и *пароль* аргументы, *UserID*  и *пароль* аргументы переопределяют значения, указанные в *ConnectionString*.  
  
 После завершения операции через открытый **подключения**, использовать [закрыть](../../../ado/reference/ado-api/close-method-ado.md) метод, чтобы освободить все связанные с ним ресурсы системы. Закрыть объект не удаляется из памяти; Вы можете изменить настройки его свойств и использовать **откройте** метод, чтобы открыть его позже. Чтобы полностью исключить объект из памяти, присвоить переменной объекта *ничего не*.  
  
> [!NOTE]
>  **Удаленное использование службы данных** при использовании на стороне клиента **подключения** объекта, **откройте** метод не фактически установить подключение к серверу до [набора записей ](../../../ado/reference/ado-api/recordset-object-ado.md) открывается на **подключения** объекта.  
  
> [!NOTE]
>  URL-адреса, с использованием схемы http, автоматически вызывает метод [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов Open и Close (Visual Basic)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Примеры методов Open и Close (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Примеры методов Open и Close (Visual C++)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Метод Open (объект Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Метод Open (объект Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Метод Open (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Метод OpenSchema](../../../ado/reference/ado-api/openschema-method.md)
