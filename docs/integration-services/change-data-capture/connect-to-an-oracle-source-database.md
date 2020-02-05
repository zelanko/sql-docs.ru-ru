---
title: Соединение с базой данных-источником Oracle | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- oraDb
ms.assetid: 220cf555-0db2-443c-8f87-8e413f3ca731
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d49ffcf03fab810eefd190ffea91aa3e5ff38cfe
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71298849"
---
# <a name="connect-to-an-oracle-source-database"></a>Соединение с базой данных-источником Oracle

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  На странице «Источник Oracle» указываются сведения, необходимые для соединения с базой данных-источником Oracle. Экземпляр CDC считывает журналы повторов базы данных Oracle, с которой установлено соединение.  
  
 **Строка подключения Oracle**  
 Введите строку подключения Oracle для компьютера, на котором установлена используемая база данных Oracle. Строка подключения указывается одним из следующих способов.  
  
 `host[:port][/service name]`  
  
 В строке подключения также можно указать дескриптор соединения Oracle Net, например `(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp) (HOST=erp.contoso.com) (PORT=1521)) (CONNECT_DATA=(SERVICE_NAME=orcl)))`  
  
 Если используется сервер каталогов или файл tnsname, то строкой подключения может быть имя соединения.  
  
 **Проверка подлинности интеллектуального анализа журналов Oracle**  
 Чтобы ввести учетные данные проверки подлинности для пользователя базы данных Oracle, который имеет право выполнять интеллектуальный анализ журналов, выберите один из следующих вариантов.  
  
-   **Проверка подлинности Windows**. Выберите этот параметр, чтобы использовать учетные данные текущего пользователя Windows. Этот параметр можно использовать только в том случае, если в базе данных Oracle настроено использование проверки подлинности Windows.  
  
-   **Проверка подлинности Oracle**. При выборе этого варианта необходимо ввести **Имя пользователя** и **Пароль** пользователя в базе данных Oracle, с которой устанавливается соединение.  
  
> [!NOTE]
>  Для выполнения интеллектуального анализа журналов пользователь должен иметь следующие права доступа, предоставленные в базе данных Oracle.  
> 
>  -   SELECT на \<любая-отслеживаемая-таблица>  
> -   SELECT ANY TRANSACTION  
> -   EXECUTE на DBMS LOGMNR  
> -   SELECT на V$LOGMNR CONTENTS  
> -   SELECT на V$ARCHIVED LOG  
> -   SELECT на V$LOG  
> -   SELECT на V$LOGFILE  
> -   SELECT на V$DATABASE  
> -   SELECT на V$THREAD  
> -   SELECT на ALL INDEXES  
> -   SELECT на ALL OBJECTS  
> -   SELECT на DBA OBJECTS  
> -   SELECT на ALL TABLES  
> 
>  Если какое-либо из этих прав доступа нельзя предоставить V$xxx, предоставьте его V_S$xxx.  
  
 **Проверка соединения**  
 Нажмите кнопку **Проверить соединение** , чтобы определить возможность соединения с удаленным компьютером, на котором находится база данных Oracle. Откроется диалоговое окно, в котором будет указано, удалось ли установить соединение.  
  
> [!IMPORTANT]  
>  Из-за известной проблемы соединение с базой данных-источником Oracle может быть не установлено, если конструктор CDC был запущен не от имени администратора. Если установить соединение не удается, закройте и перезапустите конструктор CDC через пункт меню **Запуск от имени администратора** .  
  
 Завершив ввод данных на этой странице, нажмите кнопку **Далее** , чтобы перейти на страницу [Select Oracle Tables and Columns](../../integration-services/change-data-capture/select-oracle-tables-and-columns.md).  
  
## <a name="see-also"></a>См. также:  
 [Как создать экземпляр изменения базы данных SQL Server](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)   
 [Изменение свойств экземпляра](../../integration-services/change-data-capture/edit-instance-properties.md)  
  
  
