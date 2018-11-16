---
title: Включение библиотеки DLL для работы на DCOM | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DLL on DCOM in RDS [ADO]
- DCOM in RDS [ADO]
- business objects in RDS [ADO]
ms.assetid: 5f1c2205-191c-4fb4-9bd9-84c878ea46ed
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e45dff30c67f94abb58afcf19d151dd02d33c161
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2018
ms.locfileid: "51559731"
---
# <a name="enabling-a-dll-to-run-on-dcom"></a>Разрешение запуска библиотеки DLL в DCOM
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Ниже показано, как включить DLL-файл объекта бизнеса использование DCOM и Microsoft Internet сведения службы (HTTP) с помощью служб компонентов.  
  
1.  Создайте новый пустой пакет в оснастке MMC служб компонентов.  
  
     Будет использовать оснастки MMC служб компонентов для создания пакета и добавить DLL-ФАЙЛ в этот пакет. Это делает доступными через DCOM DLL-файл, но он удаляет доступность через IIS. (Если вы установите в реестре для DLL-файл, **Inproc** ключ теперь является пустым; присвоение атрибуту активации, описано далее в этом разделе добавляет значение в **Inproc** ключ.)  
  
2.  Установите бизнес-объект в пакет.  
  
     -или-  
  
     Импорт [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) объект в пакет.  
  
3.  Установите для атрибута активации для пакета **в процессе создателя** (библиотека приложение).  
  
     Чтобы делать DLL-файл, доступными через DCOM и IIS на одном компьютере, необходимо задать атрибут активации компонента в оснастке MMC служб компонентов. После выбора атрибута **в процессе создателя**, можно будет заметить, что **Inproc** ключ сервера в реестре была добавлена, точек к службам компонента суррогатной .dll.  
  
 Дополнительные сведения о служб компонентов (или служба Microsoft Transaction, если вы используете Windows NT) и как выполнить эти действия, посетите веб-узел Microsoft Web Server транзакции.


