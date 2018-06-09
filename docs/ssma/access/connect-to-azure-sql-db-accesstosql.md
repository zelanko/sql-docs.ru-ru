---
title: Подключения к базе данных Azure SQL (AccessToSQL) | Документы Microsoft
ms.prod: sql
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Connect to SQL Azure dialog box
ms.assetid: bf44b236-d9be-41ae-a5fd-bd73038e505f
caps.latest.revision: 17
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d61eab04dffa1723c6d77a118033eee535a917e2
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34773450"
---
# <a name="connect-to-azure-sql-db-accesstosql"></a>Подключения к базе данных Azure SQL (AccessToSQL)
Подключения в SQL Azure-диалоговое окно можно используйте для подключения к базе данных SQL Azure, которые требуется перенести.  
  
Чтобы открыть это диалоговое окно на **файл** последовательно выберите пункты **подключение к SQL Azure**. Если ранее вы подключились, команда является **повторно подключиться к SQL Azure.**  
  
## <a name="options"></a>Параметры  
**Имя сервера**  
  
Выберите или введите имя сервера для подключения к SQL Azure.  
  
**База данных**  
  
Выберите, введите или **Обзор** имя базы данных.  
  
> [!IMPORTANT]  
> SSMA для Access не поддерживает подключение к базе данных master в SQL Azure.  
  
**Имя пользователя**  
  
Введите имя пользователя, который будет использоваться SSMA для подключения к базе данных SQL Azure  
  
**Пароль**  
  
Введите пароль для имени пользователя.  
  
**Шифрование**  
  
SSMA рекомендует зашифрованное соединение с SQL Azure.  
  
## <a name="create-azure-database"></a>Создание базы данных SQL Azure  
Для создания новой базы данных azure, выполните следующие действия  
  
1.  Нажмите кнопку обзора, который присутствует в окне подключения к SQL Azure-диалоговое окно  
  
2.  Если нет никаких баз данных, отображаются два элемента меню  
  
    1.  **(не найдены базы данных)**  которого отключено и серым все время  
  
    2.  **Создать новую базу данных** всегда включен, позволяя пользователям для создания новой базы данных azure в учетной записи SQL Azure. При выборе этого пункта меню, создание базы данных SQL azure используется диалоговое окно с их именем базы данных и размер.  
  
3.  Во время создания базы данных эти два параметра указан в качестве входных данных.  
  
    1.  **Имя базы данных:** введите имя базы данных.  
  
    2.  **Размер базы данных:** выбрать размер базы данных, который необходимо создать в учетной записи SQL Azure.  
  
