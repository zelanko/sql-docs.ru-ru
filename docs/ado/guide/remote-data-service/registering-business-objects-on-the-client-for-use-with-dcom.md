---
title: Регистрация бизнес-объектов на стороне клиента для использования с DCOM | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- business objects in RDS [ADO]
ms.assetid: 75a21910-607f-463a-ae18-a17130dafb7e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 999eb43304150c9af8d61be591f3c4c0ab62566f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929850"
---
# <a name="registering-business-objects-on-the-client-for-use-with-dcom"></a>Регистрация бизнес-объектов в клиенте для использования с DCOM
Настраиваемые бизнес-объекты должны гарантировать, что на стороне клиента можно сопоставить их имя программы (ProgId) с идентификатором (CLSID), который может использоваться через DCOM. По этой причине идентификатор ProgID объекта DCOM должно быть в реестре клиентского и сопоставить с Идентификатором класса серверных бизнес-объекта. Для других поддерживаемых протоколов (HTTP, HTTPS и внутри процесса) это не является обязательным.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Например если предоставить серверной бизнес-объект, называемый MyBObj с Идентификатором определенного класса, например, «{00112233-4455-6677-8899-00AABBCCDDEE}», убедитесь, что следующие записи добавляются в реестр на стороне клиента:  
  
```console
[HKEY_CLASSES_ROOT]  
\MyBObj\Clsid\(Default) "{00112233-4455-6677-8899-00AABBCCDDEE}"  
```


