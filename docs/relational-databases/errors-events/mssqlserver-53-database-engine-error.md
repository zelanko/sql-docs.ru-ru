---
title: "MSSQLSERVER_53 | Документация Майкрософт"
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
- "53"
helpviewer_keywords:
- 53 (Database Engine error)
ms.assetid: 1234f5a2-b3d1-425a-b29f-480fa792305f
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 2c415a8e19d463194764a3d78ab538782c74e721
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver53"></a>MSSQLSERVER_53
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|53|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя||  
|Текст сообщения|При соединении с сервером произошла ошибка.  Эта ошибка при соединении с SQL Server может быть вызвана тем, что в параметрах SQL Server по умолчанию запрещены удаленные соединения. (поставщик: поставщик именованных каналов, ошибка: 40: Не удалось открыть соединение с SQL Server) (поставщик данных .Net SqlClient)|  
  
## <a name="explanation"></a>Объяснение  
Клиенту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удается установить соединение с сервером. Эта ошибка может возникать в том случае, если клиенту не удается преобразовать имя сервера либо если указано неверное имя сервера.  
  
## <a name="user-action"></a>Действие пользователя  
Убедитесь, что в клиенте введено правильное имя сервера, а также в том, что удается преобразовать имя сервера от клиента. Разрешение имен TCP/IP можно проверить с помощью команды **ping** в операционной системе Windows.  
  
## <a name="see-also"></a>См. также:  
[Сетевые протоколы и библиотеки](~/sql-server/install/network-protocols-and-network-libraries.md)  
[Конфигурация клиентской сети](~/database-engine/configure-windows/client-network-configuration.md)  
[Настройка клиентских протоколов](~/database-engine/configure-windows/configure-client-protocols.md)  
[Включение или отключение сетевого протокола сервера](~/database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  

