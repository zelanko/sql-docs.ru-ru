---
title: Создание допустимой строки подключения с использованием протокола общей памяти | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine], shared memory
- aliases [SQL Server], shared memory
ms.assetid: 5fff42e8-377f-4b40-b0c8-b02393f8a1af
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: caebb35ed8dfb3eee67c5371ff9ffb4078311546
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51656944"
---
# <a name="creating-a-valid-connection-string-using-shared-memory-protocol"></a>Создание допустимой строки соединения с использованием протокола общей памяти
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  При подключении к [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с клиента, запущенного на том же компьютере, используется протокол общей памяти. У общей памяти нет настраиваемых свойств. Протокол общей памяти всегда используется первым и его нельзя переместить с верхней строчки списка **Включенные протоколы** окна **Свойства клиентских протоколов** . Протокол общей памяти может быть отключен, что бывает полезным при устранении неполадок в одном из других протоколов.  
  
 При помощи протокола общей памяти нельзя создать псевдоним, но если протокол общей памяти включен, то во время подключения к компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)] по имени создается соединение общей памяти. В строке подключения общей памяти используется формат `lpc:<servername>[\instancename]`.  
  
## <a name="connecting-to-the-local-server"></a>Подключение к локальному серверу  
 При подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запущенному на том же компьютере, что и клиент, в качестве имени сервера можно использовать **(local)** . Это действие не рекомендуется, поскольку может вызвать неоднозначность, но может быть полезным, если известно, что клиент запущен на нужном компьютере. Например, при создании приложения для мобильных отключенных пользователей, таких как торговый персонал, когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет запускаться на переносных компьютерах и использоваться для хранения данных проекта, клиент, подключающийся к **(local)** , будет всегда подключаться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , выполняющемуся на переносном компьютере. Вместо **(local)** можно использовать слово**localhost**или точку ( **.**).  
  
## <a name="verifying-your-connection-protocol"></a>Проверка протокола соединения  
 Следующий запрос возвратит протокол, используемый в текущем соединении.  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a>Примеры:  
 Следующие имена будут подключаться к локальному компьютеру при помощи протокола общей памяти, если он включен:  
  
 `<servername>`  
  
 `<servername>\<instancename>`  
  
 `(local)`  
  
 `localhost`  
  
 Невозможно создать псевдоним для соединения по протоколу общей памяти.  
  
> [!NOTE]  
>  При указании IP-адреса в поле **Сервер** будет установлено соединение TCP/IP.  
  
## <a name="see-also"></a>См. также:  
 [Создание допустимой строки подключения с использованием протокола TCP/IP](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)   
 [Создание допустимой строки подключения, использующей протокол именованных каналов](https://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)   
 [Выбор сетевого протокола](https://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)  
  
  
