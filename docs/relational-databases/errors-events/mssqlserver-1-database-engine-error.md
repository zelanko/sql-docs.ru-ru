---
title: "MSSQLSERVER_ 1 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- "-1"
helpviewer_keywords:
- -1 (Database Engine error)
ms.assetid: bad25b91-eaed-46c0-a5b7-71117a32304c
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d4ad7c2405b50c97e9d26f047089bc5069a3bc20
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver-1"></a>MSSQLSERVER_-1
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|-1|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя||  
|Текст сообщения|При соединении с сервером произошла ошибка.  При подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] эта ошибка может быть вызвана тем, что в конфигурации по умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает удаленные соединения. (поставщик: сетевые интерфейсы SQL, ошибка: 28 — Сервер не поддерживает запрашиваемый протокол) (Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ошибка: -1)|  
  
## <a name="explanation"></a>Объяснение  
Клиенту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удается установить соединение с сервером. Возможны следующие причины возникновения этой ошибки.  
  
-   Указанное имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] недопустимо.  
  
-   Протокол именованных каналов или TCP не включен.  
  
-   Брандмауэр на сервере отклонил это соединение.  
  
-   Служба "Браузер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]" (sqlbrowser) не запущена.  
  
## <a name="user-action"></a>Действие пользователя  
Чтобы устранить эту неполадку, выполните следующие действия.  
  
-   Проверьте правильность указания имени экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которое указано в строке соединения.  
  
-   С помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настройте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на прием удаленных соединений по протоколу TCP или по протоколам именованных каналов. Дополнительные сведения о приеме удаленных соединений см. в статье [Включение или отключение сетевого протокола сервера](~/database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md).  
  
-   Убедитесь, что в брандмауэре на экземпляре сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] открыты порты для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и порт браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (UDP-порт 1434).  
  
-   Убедитесь, что служба «[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], браузер» запущена на сервере.  
  
## <a name="see-also"></a>См. также:  
[Настройка брандмауэра Windows для доступа к ядру СУБД](~/database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)  
[Настройка клиентских протоколов](~/database-engine/configure-windows/configure-client-protocols.md)  
[Сетевые протоколы и библиотеки](~/sql-server/install/network-protocols-and-network-libraries.md)  
[Конфигурация клиентской сети](~/database-engine/configure-windows/client-network-configuration.md)  
[Настройка клиентских протоколов](~/database-engine/configure-windows/configure-client-protocols.md)  
[Включение или отключение сетевого протокола сервера](~/database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  

