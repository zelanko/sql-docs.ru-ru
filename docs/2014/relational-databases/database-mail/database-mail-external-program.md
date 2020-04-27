---
title: Внешняя программа компонента Database Mail | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- external programs [Database Mail]
- DatabaseMail90.exe
- Database Mail [SQL Server], external programs
ms.assetid: bc124164-eb6e-4b7f-bf66-98a3113d02f7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6c617e4f7c069a869935fa4ed83d28c02d0b0b9a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62917645"
---
# <a name="database-mail-external-program"></a>Внешняя программа компонента Database Mail
  Внешним исполняемым файлом компонента Database Mail является файл **DatabaseMail.exe**, находящийся в подкаталоге **MSSQL\Binn** каталога установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Компонент Database Mail использует активацию компонента Service Broker для запуска внешней программы, когда нужно выполнить обработку электронных сообщений. Компонент Database Mail запускает один экземпляр внешней программы. Внешняя программа выполняется в контексте безопасности учетной записи службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **В этом разделе.**  
  
-   [Основные понятия внешней программы компонента Database Mail](#ComponentsAndConcepts)  
  
-   [Задачи, связанные с настройкой внешней программы компонента Database Mail](#RelatedTasks)  
  
##  <a name="database-mail-external-program-concepts"></a><a name="ComponentsAndConcepts"></a> Основные понятия внешней программы компонента Database Mail  
 При запуске внешняя программа подключается к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , используя проверку подлинности Windows, и начинает обработку электронных сообщений. Если в течение указанного времени ожидания сообщений для отправки нет, программа завершает работу. Период времени, в течение которого программа будет ожидать сообщений до завершения работы, можно настроить или с помощью мастера настройки, или с помощью хранимых процедур компонента Database Mail. Дополнительные сведения см. в разделе [sysmail_configure_sp (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql).  
  
 Внешняя программа хранит данные в системных таблицах базы данных **msdb** . Если внешняя программа не может взаимодействовать с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], она регистрирует ошибки в журнале событий приложений Microsoft Windows. Дополнительная регистрация сообщений используется, если для уровня ведения журнала в диалоговом окне **Установка системных параметров** **мастера настройки компонента Database Mail** установлено значение **Подробный**.  
  
 Обратите внимание, что для повышения эффективности внешняя программа кэширует сведения об учетной записи и профиле. Поэтому изменения конфигурации учетных записей и профилей могут не отражаться во внешней программе в течение нескольких минут.  
  
##  <a name="tasks-related-to-configuring-database-mail-external-program"></a><a name="RelatedTasks"></a> Задачи, связанные с настройкой внешней программы компонента Database Mail  
  
|Задача конфигурации|Ссылка на раздел|  
|------------------------|----------------|  
|Указание времени, используемого внешней программой перед выходом.|[sysmail_configure_sp (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql)|  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)   
 [Ведение журнала и аудит компонента Database Mail](database-mail-log-and-audits.md)   
 [Database Mail](database-mail.md)  
  
  
