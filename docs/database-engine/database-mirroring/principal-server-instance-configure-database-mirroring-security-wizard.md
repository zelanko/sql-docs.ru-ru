---
title: "Экземпляр основного сервера (мастер настройки безопасности зеркального отображения баз данных) | Документы Майкрософт"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.configdbmsecurwiz.principalsrvr.f1
ms.assetid: 58af27d7-c5dd-4669-be6b-b472bc2c8ef4
caps.latest.revision: "36"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 80f5c385f6544345259413b56ac90932c67058ef
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="principal-server-instance-configure-database-mirroring-security-wizard"></a>Экземпляр основного сервера (мастер настройки безопасности зеркального отображения баз данных)
  Используйте данную страницу для задания данных об экземпляре сервера основной базы данных. Основная база данных представляет собой копию базы данных, начинающую сеанс зеркального отображения. После начала сеанса основная база данных является копией базы данных, принимающей пользовательские изменения. (При отработке отказа основная роль и роль зеркального отображения меняются местами, следовательно, первоначальная основная база данных может не остаться основной.)  
  
 **Настройка зеркального отображения базы данных в среде SQL Server Management Studio**  
  
-   [Создание сеанса зеркального отображения базы данных с использованием проверки подлинности Windows (среда SQL Server Management Studio)](../../database-engine/database-mirroring/establish-database-mirroring-session-windows-authentication.md)  
  
-   [Запуск мастера настройки безопасности зеркального отображения баз данных (среда SQL Server Management Studio)](../../database-engine/database-mirroring/start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>Параметры  
 **Экземпляр основного сервера**  
 Поскольку зеркальное отображение базы данных в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] всегда настраивается с основного сервера, то текущим экземпляром сервера всегда будет экземпляр основного сервера.  
  
 **Прослушивающий порт**  
 Поведение этого параметра зависит от того, существует ли конечная точка зеркального отображения для этого экземпляра сервера.  
  
-   Если прослушиваемый порт не существует для данного экземпляра сервера, то в текстовом поле **Порт** отображается номер порта 5022. Можно использовать любой допустимый номер порта, например 7022.  
  
-   Если конечная точка зеркального отображения уже существует, отображается номер порта конечной точки. Если необходимо изменить порт, используйте команду ALTER ENDPOINT. Дополнительные сведения см. в разделе [ALTER ENDPOINT (Transact-SQL)](../../t-sql/statements/alter-endpoint-transact-sql.md).  
  
> [!NOTE]  
>  Номер порта обязателен.  
  
 **Имя конечной точки**  
 Если для данного экземпляра сервера существует конечная точка зеркального отображения, то здесь отображается имя конечной точки. Если конечная точка отсутствует, можно задать имя конечной точки.  
  
 **Шифровать данные, проходящие через эту конечную точку**  
 По умолчанию шифрование включено. Если этот параметр включен, шифрование обязательно (а не просто поддерживается), а для всех параметров шифрования используются значения по умолчанию. Дополнительные сведения см. в разделе [CREATE ENDPOINT (Transact-SQL)](../../t-sql/statements/create-endpoint-transact-sql.md).  
  
 Снимите этот флажок для выключения шифрования. Установите этот флажок, чтобы вновь включить шифрование.  
  
## <a name="see-also"></a>См. также:  
 [Конечная точка зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [Свойства базы данных (страница "Зеркальное отображение")](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Создание конечной точки зеркального отображения базы данных с проверкой подлинности Windows (Transact-SQL)](../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)   
 [Запуск монитора зеркального отображения баз данных (среда SQL Server Management Studio)](../../database-engine/database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Зеркальное отображение базы данных (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
