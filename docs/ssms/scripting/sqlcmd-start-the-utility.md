---
title: Запуск программу sqlcmd
description: Узнайте, как запустить программу sqlcmd, которая позволяет вводить инструкции Transact-SQL, системные процедуры и файлы скриптов, в режиме SQLCMD или в скриптах и заданиях.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.technology: ssms
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 00d57437-7a29-4da1-b639-ee990db055fb
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c305ebb95a57f8686fb2dbc49e125e7ca09d844e
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97408550"
---
# <a name="sqlcmd---start-the-utility"></a>sqlcmd — запуск служебной программы
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
  [Программа sqlcmd](../../tools/sqlcmd-utility.md) позволяет вводить инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], системные процедуры и файлы скриптов из командной строки в редактор запросов в режиме SQLCMD, в файл скрипта Windows или шаг задания операционной системы (Cmd.exe) задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
> [!NOTE]  
>  По умолчанию в программе **sqlcmd** используется проверка подлинности Windows. Для использования проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требуется указать имя пользователя и пароль, применяя параметры **-U** и **-P** .  
  
> [!NOTE]  
>  По умолчанию [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] устанавливается как именованный экземпляр с именем **sqlexpress**.  
  
### <a name="start-the-sqlcmd-utility-and-connect-to-a-default-instance-of-sql-server"></a>Запуск программы sqlcmd и подключение к экземпляру SQL Server по умолчанию  
  
1.  В меню **Пуск** выберите команду **Выполнить**. В поле **Открыть** введите **cmd**, а затем нажмите кнопку **ОК** , чтобы открыть окно командной строки. (Если подключение к этому экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] не было выполнено, возможно, потребуется настроить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на прием подключений.)  
  
2.  В командной строке введите **sqlcmd**.  
  
3.  Нажмите клавишу ВВОД.  
  
     Теперь установлено доверительное соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию, запущенным на этом компьютере.  
  
     **1>** — это запрос программы **sqlcmd**, который указывает номер строки. При каждом нажатии клавиши ВВОД номер увеличивается на единицу.  
  
4.  Чтобы завершить сеанс **sqlcmd** , введите **EXIT** в запросе **sqlcmd** .  
  
### <a name="start-the-sqlcmd-utility-and-connect-to-a-named-instance-of-sql-server"></a>Запуск служебной программы sqlcmd и подключение к именованному экземпляру SQL Server  
  
1.  Откройте окно командной строки и введите **sqlcmd -S**_мойСервер\имяЭкземпляра_. Замените *мойСервер\имяЭкземпляра* именем компьютера и экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , с которым нужно соединиться.  
  
2.  Нажмите клавишу ВВОД.  
  
     Запрос программы **sqlcmd** (1>) указывает, что установлено подключение к указанному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    > [!NOTE]  
    >  Введенные инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] хранятся в буфере. Они выполняются как пакет при обнаружении команды GO.  
  
## <a name="see-also"></a>См. также:  
 [Выполнение файлов скрипта Transact-SQL с использованием программы sqlcmd](./sqlcmd-run-transact-sql-script-files.md)  
  
