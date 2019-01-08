---
title: Увеличение размера базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], size
- increasing database size
- database size [SQL Server], increasing
- size [SQL Server], databases
ms.assetid: 14f4206d-3afa-4ba9-9849-23e81d63306d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 02a34ba1e0f441b665c239d60f6398afa4247102
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52808996"
---
# <a name="increase-the-size-of-a-database"></a>Увеличение размера базы данных
  Этот подраздел описывает, как увеличить размер базы данных [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. База данных расширяется или путем увеличения размера существующих данных либо файла журнала, или путем добавления нового файла к базе данных.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Увеличение размера базы данных с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Добавить или удалить файл во время выполнения инструкции BACKUP невозможно.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER на базу данных.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-increase-the-size-of-a-database"></a>Увеличение размера базы данных  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Разверните узел **Базы данных**, щелкните правой кнопкой мыши базу данных, размер которой необходимо увеличить, и выберите пункт **Свойства**.  
  
3.  В окне **Свойства базы данных**выберите страницу **Файлы** .  
  
4.  Чтобы увеличить размер существующего файла, увеличьте значение в столбце **Исходный размер (МБ)** для файла. Необходимо увеличить размер базы данных, по крайней мере, на 1 мегабайт.  
  
5.  Чтобы увеличить размер базы данных путем добавления нового файла, нажмите кнопку **Добавить** и введите значения для нового файла. Дополнительные сведения см. в статье [Добавление файлов данных или журналов в базу данных](add-data-or-log-files-to-a-database.md).  
  
6.  Нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-increase-the-size-of-a-database"></a>Увеличение размера базы данных  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере увеличивается размер файла `test1dat3`.  
  
 [!code-sql[DatabaseDDL#AlterDatabase5](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase5)]  
  
 Дополнительные сведения см. в разделе [Параметры инструкции ALTER DATABASE для файлов и файловых групп (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options).  
  
## <a name="see-also"></a>См. также  
 [Добавление файлов данных или журналов в базу данных](add-data-or-log-files-to-a-database.md)   
 [Сжатие базы данных](shrink-a-database.md)  
  
  
