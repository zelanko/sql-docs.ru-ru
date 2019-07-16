---
title: Метод CopyRecord (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_CopyRecord
- _Record::CopyRecord
helpviewer_keywords:
- CopyRecord method [ADO]
ms.assetid: b9bcf272-3c74-479f-95dd-0229a32e98fc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: aaabb32234cefe2e3c3727ce5a18dd2d98549a77
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67933414"
---
# <a name="copyrecord-method-ado"></a>Метод CopyRecord (ADO)
Копирует сущности, представленной [записи](../../../ado/reference/ado-api/record-object-ado.md) в другое расположение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Record.CopyRecord (Source, Destination, UserName, Password, Options, Async)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Source*  
 Необязательный параметр. Объект **строка** значение, содержащее URL-адрес задании сущности для копирования (например, файл или каталог). Если *источника* опущен или указывает на пустую строку, файл или каталог, представленный текущим [записи](../../../ado/reference/ado-api/record-object-ado.md) будут скопированы.  
  
 *Назначение*  
 Необязательный параметр. Объект **строка** значение, содержащее URL-адрес, место, где *источника* будут скопированы.  
  
 *UserName*  
 Необязательный параметр. Объект **строка** значение, содержащее идентификатор пользователя, при необходимости, разрешает доступ к *назначения*.  
  
 *Пароль*  
 Необязательный параметр. Объект **строка** значение, содержащее пароль, который при необходимости, проверяет ли *UserName*.  
  
 *Параметры*  
 Необязательный. Объект [CopyRecordOptionsEnum](../../../ado/reference/ado-api/copyrecordoptionsenum.md) значение, которое имеет значение по умолчанию **adCopyUnspecified**. Задает поведение этого метода.  
  
 *Async*  
 Необязательный. Объект **логическое** значением, которое при **True**, указывает, что эта операция должна быть асинхронной.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** значение, которое обычно возвращает значение *назначения*. Тем не менее возвращаемое точное значение зависит от поставщика.  
  
## <a name="remarks"></a>Примечания  
 Значения *источника* и *назначения* не должно быть идентичны; в противном случае возникает ошибка времени выполнения. По крайней мере одно из имен сервера, путь или ресурс должен отличаться.  
  
 Все дочерние элементы (например, подкаталоги) *источника* имеют скопированный рекурсивно, в том случае, если **adCopyNonRecursive** указан. В операцию рекурсивного *назначения* не должно быть подкаталог *источника*; в противном случае операция не будет завершена.  
  
 Этот метод завершается ошибкой, если *назначения* идентифицирует сущность (например, файл или каталог), если не **adCopyOverWrite** указан.  
  
> [!IMPORTANT]
>  Используйте **adCopyOverWrite** параметр осмотрительно. Например, задание этого параметра, при копировании файлов в каталог будет *удалить* каталога и замените его файл.  
  
> [!NOTE]
>  URL-адреса, с использованием схемы http, автоматически вызывает метод [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)
