---
title: Метод Open (подключение ADO) | Документация Майкрософт
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
ms.openlocfilehash: 15115313613ea8f86dd2267c6be3c231cab92503
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67931931"
---
# <a name="open-method-ado-connection"></a>Метод Open (объект Connection ADO)
Открывает соединение с источником данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
connection.Open ConnectionString, UserID, Password, Options  
```  
  
#### <a name="parameters"></a>Параметры  
 *ConnectionString*  
 Необязательный параметр. **Строковое** значение, содержащее сведения о соединении. Сведения о допустимых параметрах см. в свойстве [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) .  
  
 *UserID*  
 Необязательный параметр. **Строковое** значение, содержащее имя пользователя, используемое при установлении соединения.  
  
 *Пароль*  
 Необязательный параметр. **Строковое** значение, содержащее пароль, используемый при установлении соединения.  
  
 *Параметры*  
 Необязательный параметр. Значение [коннектоптионенум](../../../ado/reference/ado-api/connectoptionenum.md) , которое определяет, должен ли этот метод возвращаться после (синхронно) или до (асинхронно) установления соединения.  
  
## <a name="remarks"></a>Remarks  
 Использование метода **Open** для объекта [Connection](../../../ado/reference/ado-api/connection-object-ado.md) устанавливает физическое соединение с источником данных. После успешного завершения этого метода подключение будет активно, и вы сможете выполнить команды для него и обработать результаты.  
  
 Используйте необязательный аргумент *ConnectionString* , чтобы указать либо строку подключения, содержащую последовательность *аргументов аргумента* *= значение* , разделенную точкой с запятой, либо файл или ресурс каталога, определенный с помощью URL-адреса. Свойство **ConnectionString** автоматически наследует значение, используемое для аргумента *ConnectionString* . Поэтому можно либо задать свойство **ConnectionString** объекта **соединения** перед его открытием, либо использовать аргумент *ConnectionString* для задания или переопределения текущих параметров соединения во время вызова метода **Open** .  
  
 При передаче сведений о пользователях и паролях в аргументе *ConnectionString* и в необязательных *аргументах* *UserID* и Password аргументы *UserID* и *Password* переопределят значения, указанные в *ConnectionString*.  
  
 Когда вы завершите операции с открытым **подключением**, используйте метод [Close](../../../ado/reference/ado-api/close-method-ado.md) , чтобы освободить все связанные системные ресурсы. Закрытие объекта не приводит к его удалению из памяти; Вы можете изменить его параметры свойств и открыть его позже с помощью метода **Open** . Чтобы полностью исключить объект из памяти, присвойте переменной объекта значение *Nothing*.  
  
> [!NOTE]
>  **Использование удаленной службы данных** При использовании объекта **подключения** на стороне клиента метод **Open** не устанавливает соединение с сервером до тех пор, пока в объекте **Connection** не будет открыт [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
> [!NOTE]
>  URL-адреса, использующие схему HTTP, автоматически вызывают [поставщик OLE DB Майкрософт для публикации в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Примеры методов Open и Close (Visual Basic)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Пример методов Open и Close (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Пример методов Open и Close (Visual c++)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Метод Open (запись ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Метод Open (набор записей ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Метод Open (поток ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Метод OpenSchema](../../../ado/reference/ado-api/openschema-method.md)
