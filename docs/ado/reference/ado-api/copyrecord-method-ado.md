---
title: Метод CopyRecord (ADO) | Документы Microsoft
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
apitype: COM
f1_keywords:
- _Record::raw_CopyRecord
- _Record::CopyRecord
helpviewer_keywords:
- CopyRecord method [ADO]
ms.assetid: b9bcf272-3c74-479f-95dd-0229a32e98fc
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 96ce055d28959d2846e954423340164536df50e3
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="copyrecord-method-ado"></a>Метод CopyRecord (ADO)
Копирует сущности, представленной [записи](../../../ado/reference/ado-api/record-object-ado.md) в другое место.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Record.CopyRecord (Source, Destination, UserName, Password, Options, Async)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Source*  
 Необязательно. Объект **строка** значение, содержащее URL-адрес задании сущности для копирования (например, файл или каталог). Если *источника* опущен или указывает на пустую строку, файл или каталог, представленный текущим [записи](../../../ado/reference/ado-api/record-object-ado.md) будут скопированы.  
  
 *Назначение*  
 Необязательно. Объект **строка** значение, содержащее URL-адрес, указывающий местоположение где *источника* будут скопированы.  
  
 *UserName*  
 Необязательно. Объект **строка** значение, содержащее идентификатор пользователя, при необходимости, дающая право на доступ к *назначения*.  
  
 *Пароль*  
 Необязательно. Объект **строка** значение, содержащее пароль, при необходимости проверяет *UserName*.  
  
 *Параметры*  
 Необязательно. Объект [CopyRecordOptionsEnum](../../../ado/reference/ado-api/copyrecordoptionsenum.md) значение, которое имеет значение по умолчанию **adCopyUnspecified**. Задает поведение данного метода.  
  
 *Асинхронный*  
 Необязательно. Объект **логическое** значением, которое при **True**, указывает, что эта операция должна быть асинхронной.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** значение, которое обычно возвращает значение *назначения*. Тем не менее возвращаемое точное значение зависит от поставщика.  
  
## <a name="remarks"></a>Замечания  
 Значения *источника* и *назначения* не должна одинаковы; в противном случае возникает ошибка времени выполнения. По крайней мере одно имя сервера, путь или ресурсов должны отличаться.  
  
 Все дочерние элементы (например, подкаталогов) *источника* , скопированный рекурсивно, если не **adCopyNonRecursive** указано. В операцию рекурсивного *назначения* не должно быть подкаталог *источника*; в противном случае операция не будет завершена.  
  
 Этот метод завершается ошибкой, если *назначения* идентифицирует сущность (например, файл или каталог), если не **adCopyOverWrite** указано.  
  
> [!IMPORTANT]
>  Используйте **adCopyOverWrite** параметр обдуманно. Например, задание этого параметра при копировании файлов в каталоге будут *удалить* каталог и заменить ее именем файла.  
  
> [!NOTE]
>  URL-адреса, с помощью схемы http автоматически вызывает [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)
