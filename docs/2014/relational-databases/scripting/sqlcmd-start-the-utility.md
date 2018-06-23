---
title: Запуск программы sqlcmd | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00d57437-7a29-4da1-b639-ee990db055fb
caps.latest.revision: 39
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: eb2234b466a41b58cc1dd137950514de4b7aa458
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36187964"
---
# <a name="start-the-sqlcmd-utility"></a>Запуск программу sqlcmd
  Чтобы начать использовать программу `sqlcmd`, требуется запустить ее и подключиться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Можно соединиться или с экземпляром, установленным по умолчанию, или с именованным экземпляром. Первый шаг — запуск программы `sqlcmd`.  
  
> [!NOTE]  
>  По умолчанию в программе `sqlcmd` используется проверка подлинности Windows. Для использования проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требуется указать имя пользователя и пароль, применяя параметры **-U** и **-P** .  
  
> [!NOTE]  
>  По умолчанию [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] устанавливается как именованный экземпляр с именем **sqlexpress**.  
  
 Если подключение к этому экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] не было выполнено, то, возможно, потребуется настроить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на прием соединений.  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-default-instance-of-sql-server"></a>Запуск программы «sqlcmd» и подключение к экземпляру SQL Server по умолчанию  
  
1.  В меню **Пуск** выберите команду **Выполнить**. В поле **Открыть** введите **cmd**, а затем нажмите кнопку **ОК** , чтобы открыть окно командной строки.  
  
2.  В командной строке введите `sqlcmd`.  
  
3.  Нажмите клавишу ВВОД.  
  
     Теперь установлено доверительное соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию, запущенным на этом компьютере.  
  
     **1 >** — `sqlcmd` приглашение, которое указывает номер строки. При каждом нажатии клавиши ВВОД номер увеличивается на единицу.  
  
4.  Для завершения `sqlcmd` сеанса, введите `EXIT` в `sqlcmd` строки.  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-named-instance-of-sql-server"></a>Запуск программы sqlcmd и соединение с именованным экземпляром SQL Server  
  
1.  Откройте командную строку окно и введите `sqlcmd -S` *Мойсервер\имяэкземпляра*. Замените *мойСервер\имяЭкземпляра* именем компьютера и экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , с которым нужно соединиться.  
  
2.  Нажмите клавишу ВВОД.  
  
     Приглашение программы `sqlcmd` (1>) указывает, что установлено соединение с указанным экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    > [!NOTE]  
    >  Введенные инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] хранятся в буфере. Они выполняются как пакет при обнаружении команды GO.  
  
## <a name="see-also"></a>См. также  
 [Выполнение файлов скрипта Transact-SQL с использованием программы sqlcmd](sqlcmd-run-transact-sql-script-files.md)  
  
  