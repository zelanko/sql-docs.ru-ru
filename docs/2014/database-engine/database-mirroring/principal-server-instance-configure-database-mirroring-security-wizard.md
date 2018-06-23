---
title: Экземпляр основного сервера (мастер настройки безопасности зеркального отображения баз данных) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.configdbmsecurwiz.principalsrvr.f1
ms.assetid: 58af27d7-c5dd-4669-be6b-b472bc2c8ef4
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a677f04c211cedf707b8e420be6958d211da71ba
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189575"
---
# <a name="principal-server-instance-configure-database-mirroring-security-wizard"></a>Экземпляр основного сервера (мастер настройки безопасности зеркального отображения баз данных)
  Используйте данную страницу для задания данных об экземпляре сервера основной базы данных. Основная база данных представляет собой копию базы данных, начинающую сеанс зеркального отображения. После начала сеанса основная база данных является копией базы данных, принимающей пользовательские изменения. (При отработке отказа основная роль и роль зеркального отображения меняются местами, следовательно, первоначальная основная база данных может не остаться основной.)  
  
 **Настройка зеркального отображения базы данных в среде SQL Server Management Studio**  
  
-   [Создание сеанса зеркального отображения базы данных с использованием проверки подлинности Windows (среда SQL Server Management Studio)](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Запуск мастера настройки безопасности зеркального отображения баз данных (среда SQL Server Management Studio)](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>Параметры  
 **Экземпляр основного сервера**  
 Поскольку зеркальное отображение базы данных в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] всегда настраивается с основного сервера, то текущим экземпляром сервера всегда будет экземпляр основного сервера.  
  
 **Прослушивающий порт**  
 Поведение этого параметра зависит от того, существует ли конечная точка зеркального отображения для этого экземпляра сервера.  
  
-   Если прослушиваемый порт не существует для данного экземпляра сервера, то в текстовом поле **Порт** отображается номер порта 5022. Можно использовать любой допустимый номер порта, например 7022.  
  
-   Если конечная точка зеркального отображения уже существует, отображается номер порта конечной точки. Если необходимо изменить порт, используйте команду ALTER ENDPOINT. Дополнительные сведения см. в статье [ALTER ENDPOINT (Transact-SQL)](/sql/t-sql/statements/alter-endpoint-transact-sql).  
  
> [!NOTE]  
>  Номер порта обязателен.  
  
 **Имя конечной точки**  
 Если для данного экземпляра сервера существует конечная точка зеркального отображения, то здесь отображается имя конечной точки. Если конечная точка отсутствует, можно задать имя конечной точки.  
  
 **Шифровать данные, проходящие через эту конечную точку**  
 По умолчанию шифрование включено. Если этот параметр включен, шифрование обязательно (а не просто поддерживается), а для всех параметров шифрования используются значения по умолчанию. Дополнительные сведения см. в разделе [CREATE ENDPOINT (Transact-SQL)](/sql/t-sql/statements/create-endpoint-transact-sql).  
  
 Снимите этот флажок для выключения шифрования. Установите этот флажок, чтобы вновь включить шифрование.  
  
## <a name="see-also"></a>См. также  
 [Конечная точка зеркального отображения базы данных (SQL Server)](the-database-mirroring-endpoint-sql-server.md)   
 [Свойства базы данных (страница "Зеркальное отображение")](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Создание конечной точки зеркального отображения базы данных с проверкой подлинности Windows (Transact-SQL)](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)   
 [Запуск монитора зеркального отображения баз данных (среда SQL Server Management Studio)](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Зеркальное отображение базы данных (SQL Server)](database-mirroring-sql-server.md)  
  
  
