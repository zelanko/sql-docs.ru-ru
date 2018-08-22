---
title: Удаление компонентов MySQL (MySQLToSql) SSMA для | Документация Майкрософт
ms.prod: sql
ms.custom: ''
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
- Uninstalling, Extension pack
- Uninstalling, SSMA for MySQL client
ms.assetid: 87cdbd49-a0c9-4b00-8a93-34188b18d11a
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: adab686126cb608ae32870a9a138720b77d212bf
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40393943"
---
# <a name="removing-the-ssma-for-mysql-components-mysqltosql"></a>Удаление компонентов SSMA для MySQL (MySQLToSql)
После завершения миграции баз данных MySQL для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], может потребоваться удаление компонентов SSMA. Клиентские компоненты можно удалить в любое время. Тем не менее если вы удалите пакет расширения из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , затем SSMA больше не будет поддерживать миграцию данных из MySQL в целевую базу данных (SQL Server/SQL Azure) с помощью обработчика переноса данных на сервере.  
  
## <a name="uninstalling-the-ssma-for-mysql-client"></a>Удаление SSMA для MySQL клиента  
SSMA можно удалить с помощью **Установка и удаление программ**.  
  
**Чтобы удалить SSMA**  
  
1.  В панели управления откройте **Установка и удаление программ**.  
  
2.  Выберите **Microsoft SQL Server Migration Assistant для MySQL**, а затем нажмите кнопку **удалить**.  
  
3.  Чтобы убедиться, что вы хотите удалить SSMA, щелкните **Да**.  
  
## <a name="uninstalling-the-extension-pack"></a>Удаление пакета расширения  
Пакет расширений можно удалить с помощью **Установка и удаление программ**.  
  
**Удалить расширение пакета**  
  
1.  В панели управления откройте **Установка и удаление программ**.  
  
2.  Выберите **Microsoft SQL Server Migration Assistant для MySQL Extension Pack**, а затем нажмите кнопку **удалить**.  
  
3.  Чтобы подтвердить, что вы хотите удалить пакет расширений, щелкните **Да**.  
  
4.  В экземплярах с страницы скрипты базы данных программы, выберите экземпляр и нажмите кнопку **Далее**.  
  
5.  На странице Параметры подключения, выберите метод проверки подлинности и нажмите кнопку **Далее**.  
  
    Проверка подлинности Windows будет использовать учетные данные Windows для входа на экземпляр объекта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При выборе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности, необходимо ввести [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа и пароль.  
  
6.  На странице завершить операцию, нажмите кнопку **ОК**.  
  
7.  На странице "Готово", нажмите кнопку **выхода**.  
  
После завершения процесса удаления можно убедиться, что объекты в **sysdb.ssma_MySQL** схемы и, возможно, всю **sysdb** базы данных, был удален с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Тем не менее, если вы используете другие продукты SSMA, они также используют **sysdb** базы данных. Если база данных существует, и вы уверены, что нет других баз данных ссылаются на объекты в этой базе данных, можно отсоединить базу данных.  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для MySQL клиента &#40;MySQLToSQL&#41;](../../ssma/mysql/installing-ssma-for-mysql-client-mysqltosql.md)  
[Установка компонентов SSMA в SQL Server](installing-ssma-components-on-sql-server-mysqltosql.md)  
  
