---
title: Определение параметров для шагов заданий Transact-SQL | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL job step
- job steps [Transact-SQL]
- SQL Server Agent jobs, Transact-SQL step
ms.assetid: b2a47057-f6fb-432b-a7b6-5d61f33a5d9c
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 2dfa72301de2d9ea1b5c526ee3a7af9fdb6fceba
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65096746"
---
# <a name="define-transact-sql-job-step-options"></a>Определение параметров для шагов заданий Transact-SQL
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описано, как определить параметры шагов заданий [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  [!INCLUDE[tsql](../../includes/tsql-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или управляющих объектов SQL Server.  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [безопасность](#Security)  
  
-   **Для определения параметров шага задания Transact-SQL с помощью:** ,  
  
    [Среда SQL Server Management Studio](#SSMS)  
  
    [Управляющие объекты SQL Server](#SMO)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Security"></a>безопасность  
Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-define-transact-sql-job-step-options"></a>Определение параметров шага задания Transact-SQL  
  
1.  В **обозревателе объектов**разверните пункт **Агент SQL Server**, затем **Задания**, щелкните правой кнопкой задание, которое необходимо изменить, и выберите **Свойства**.  
  
2.  Щелкните страницу **Шаги** , шаг задания, а затем — **Изменить**.  
  
3.  Проверьте, что в диалоговом окне **Свойства шага задания** задан тип задания **Скрипт Transact-SQL (TSQL)** , и выберите страницу **Дополнительно** .  
  
4.  Выберите из списка **Действие при успехе** действие, которое будет инициироваться при успешном выполнении задания.  
  
5.  Укажите число повторных попыток, введя число в диапазоне от 0 до 9999 в поле **Повторные попытки** .  
  
6.  Укажите интервал между повторными попытками, введя число минут в диапазоне от 0 до 9999 в поле **Интервал повтора** .  
  
7.  Выберите из списка **Действие при ошибке** действие, которое будет инициироваться при неудачном выполнении задания.  
  
8.  Если задание является скриптом [!INCLUDE[tsql](../../includes/tsql-md.md)] , возможен выбор из следующих вариантов.  
  
    -   Введите имя **файла вывода**. По умолчанию файл перезаписывается при каждом выполнении шага задания. Если не нужно перезаписывать файл вывода, поставьте флажок **Дописать выходные данные в существующий файл**. Этот параметр доступен только элементам предопределенной роли сервера **sysadmin** . Имейте в виду, что среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] не позволяет пользователям просматривать произвольные файлы файловой системы, поэтому нельзя просмотреть в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] шаги заданий, записанные в файловую систему.  
  
    -   Установите флажок **Сохранять данные журнала в таблице** , если журнал шага задания необходимо вести в таблице базы данных. По умолчанию содержимое таблицы перезаписывается при каждом выполнении шага задания. Если не нужно, чтобы содержимое таблицы перезаписывалось, поставьте флажок **Дописать выходные данные в существующую запись в таблице**. После выполнения шага задания можно просмотреть содержимое этой таблицы, нажав **Просмотр**.  
  
    -   Установите флажок **Включить в журнал выходные данные шага** , если результаты шага должны быть включены в его журнал. Результат будет отображен только в случае отсутствия ошибок. Кроме того, отображаемый результат может быть усечен.  
  
9. Если члену предопределенной роли сервера **sysadmin** нужно выполнить шаг задания в контексте другого имени входа SQL, ему следует выбрать имя входа SQL из списка **Выполнять от имени** .  
  
## <a name="SMO"></a>Использование управляющих объектов SQL Server  
**Определение параметров шага задания Transact-SQL**  
  
Воспользуйтесь классом **JobStep** на любом языке программирования, таком как Visual Basic, Visual C# или PowerShell.  
  
