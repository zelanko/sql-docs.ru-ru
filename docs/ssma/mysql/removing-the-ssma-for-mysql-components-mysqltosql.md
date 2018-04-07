---
title: Удаление SSMA для MySQL компонентов (MySQLToSql) | Документы Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Uninstalling, Extension pack
- Uninstalling, SSMA for MySQL client
ms.assetid: 87cdbd49-a0c9-4b00-8a93-34188b18d11a
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: adf008b1a6bbcd584c0d3c0ee90dcb4345cf1819
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="removing-the-ssma-for-mysql-components-mysqltosql"></a>Удаление SSMA для MySQL компонентов (MySQLToSql)
После завершения миграции баз данных MySQL для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], может потребоваться удалить компоненты SSMA. Клиентские компоненты можно удалить в любое время. Однако при удалении пакета расширения из [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , затем SSMA больше не будет поддерживать переноса данных из MySQL в целевую базу данных (SQL Server или SQL Azure) с использованием механизма серверных данных миграции.  
  
## <a name="uninstalling-the-ssma-for-mysql-client"></a>При удалении SSMA для клиента MySQL  
SSMA можно удалить с помощью **Установка и удаление программ**.  
  
**Чтобы удалить SSMA**  
  
1.  В панели управления откройте **Установка и удаление программ**.  
  
2.  Выберите **Microsoft SQL Server Migration Assistant для MySQL**, а затем нажмите кнопку **удалить**.  
  
3.  Чтобы подтвердить, что вы хотите удалить SSMA, щелкните **Да**.  
  
## <a name="uninstalling-the-extension-pack"></a>Удаление пакета расширения  
Можно удалить пакет расширения с помощью **Установка и удаление программ**.  
  
**Чтобы удалить пакет расширения**  
  
1.  В панели управления откройте **Установка и удаление программ**.  
  
2.  Выберите **Microsoft SQL Server Migration Assistant для MySQL пакета расширения**, а затем нажмите кнопку **удалить**.  
  
3.  Чтобы подтвердить удаление пакета расширения, нажмите кнопку **Да**.  
  
4.  В экземплярах с страницы скриптов базы данных программы, выберите экземпляр и нажмите кнопку **Далее**.  
  
5.  На странице Параметры подключения, выберите метод проверки подлинности и нажмите кнопку **Далее**.  
  
    Проверка подлинности Windows будет использовать учетные данные Windows для входа на экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. При выборе [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] проверки подлинности, необходимо ввести [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] имя входа и пароль.  
  
6.  На странице завершить операцию, нажмите кнопку **ОК**.  
  
7.  На странице «Готово», нажмите кнопку **выхода**.  
  
После завершения процесса удаления можно подтвердить, что объекты, в **sysdb.ssma_MySQL** схемы и весь **sysdb** базы данных, была удалена с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. Тем не менее, если вы используете другие продукты SSMA, она также использует **sysdb** базы данных. Если база данных существует, и вы уверены, что любая другая база данных ссылаются на объекты в этой базе данных, можно отсоединить базы данных.  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для клиента MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/installing-ssma-for-mysql-client-mysqltosql.md)  
[Установка компонентов SSMA в SQL Server](http://msdn.microsoft.com/en-us/6772d0c5-258f-4d7b-afb0-b5f810e71af1)  
  
