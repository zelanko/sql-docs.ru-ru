---
title: "Запуск программу sqlcmd | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00d57437-7a29-4da1-b639-ee990db055fb
caps.latest.revision: 41
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
---
# Запуск программу sqlcmd
    
> [!NOTE]  
>  По умолчанию в программе **sqlcmd** используется проверка подлинности Windows. Для использования проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требуется указать имя пользователя и пароль, применяя параметры **-U** и **-P**.  
  
> [!NOTE]  
>  По умолчанию [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] устанавливается как именованный экземпляр с именем **sqlexpress**.  
  
### Запуск программы sqlcmd и подключение к экземпляру SQL Server по умолчанию  
  
1.  В меню **Пуск** выберите команду **Выполнить**. В поле **Открыть** введите **cmd**, а затем нажмите кнопку **ОК**, чтобы открыть окно командной строки. (Если подключение к этому экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] не было выполнено, возможно, потребуется настроить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на прием подключений.)  
  
2.  В командной строке введите **sqlcmd**.  
  
3.  Нажмите клавишу ВВОД.  
  
     Теперь установлено доверительное соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию, запущенным на этом компьютере.  
  
     **1>** — это запрос программы **sqlcmd**, который указывает номер строки. При каждом нажатии клавиши ВВОД номер увеличивается на единицу.  
  
4.  Чтобы завершить сеанс **sqlcmd**, введите **EXIT** в запросе **sqlcmd**.  
  
### Запуск служебной программы sqlcmd и подключение к именованному экземпляру SQL Server  
  
1.  Откройте окно командной строки и введите **sqlcmd -S***мойСервер\имяЭкземпляра*. Замените *мойСервер\имяЭкземпляра* именем компьютера и экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], с которым нужно соединиться.  
  
2.  Нажмите клавишу ВВОД.  
  
     Запрос программы **sqlcmd** (1>) указывает, что установлено подключение к указанному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    > [!NOTE]  
    >  Введенные инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] хранятся в буфере. Они выполняются как пакет при обнаружении команды GO.  
  
## См. также:  
 [Выполнение файлов скрипта Transact-SQL с использованием программы sqlcmd](../../relational-databases/scripting/run-transact-sql-script-files-using-sqlcmd.md)  
  
  