---
description: Удаление компонентов SSMA для Oracle (OracleToSQL)
title: Удаление SSMA для компонентов Oracle (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Uninstalling the Extension Pack
ms.assetid: 8b527a56-4e52-487a-9ac9-2320388e6d7d
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: 263d04b401146ce2975a810b084e4957f1daf718
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88492415"
---
# <a name="removing-ssma--for-oracle-components-oracletosql"></a>Удаление компонентов SSMA для Oracle (OracleToSQL)
После завершения миграции баз данных из Oracle в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может потребоваться удалить компоненты SSMA. Вы можете удалить клиентские компоненты в любое время. Однако не следует удалять пакет расширений, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] если только перенесенные базы данных больше не используют функции в схеме **ssma_oracle** базы данных **сисдб** .  
  
## <a name="uninstalling-the-ssma-for-oracle-client"></a>Удаление SSMA для клиента Oracle  
Удалить SSMA можно с помощью компонента " **Установка и удаление программ**".  
  
**Удаление SSMA**  
  
1.  На панели управления и откройте элемент **Установка и удаление программ**.  
  
2.  Выберите ** [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Помощник по миграции для Oracle**и нажмите кнопку **Удалить**.  
  
3.  Чтобы подтвердить удаление SSMA, нажмите кнопку **Да**.  
  
## <a name="uninstalling-the-extension-pack"></a>Удаление пакета расширений  
Если вы уверены, что перенесенные базы данных не используют объекты в схеме **сисдб. ssma_oracle** , можно удалить пакет расширений с помощью компонента " **Установка и удаление программ**".  
  
**Удаление пакета расширений**  
  
1.  На панели управления и откройте элемент **Установка и удаление программ**.  
  
2.  Выберите **Помощник по миграции Microsoft SQL Server для пакета расширений Oracle**, а затем нажмите кнопку **Удалить**.  
  
3.  Чтобы подтвердить удаление пакета расширений, нажмите кнопку **Да**.  
  
4.  На странице экземпляры с скриптами базы данных служебных программ выберите экземпляр и нажмите кнопку **Далее**.  
  
5.  На странице Параметры соединения выберите метод проверки подлинности и нажмите кнопку **Далее**.  
  
    При проверке подлинности Windows будут использоваться учетные данные Windows для входа на экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При выборе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности необходимо ввести [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа и пароль.  
  
6.  На странице операция завершена нажмите кнопку **ОК**.  
  
7.  На странице Готово нажмите кнопку **выход**.  
  
После удаления можно подтвердить, что объекты в схеме **сисдб. ssma_oracle** и, возможно, всю базу данных **сисдб** , были удалены с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Однако при использовании других продуктов SSMA они также используют базу данных **сисдб** . Если база данных существует и вы уверены, что другие базы данных не ссылаются на объекты в этой базе данных, можно отключить базу данных.  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для клиента Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[Установка компонентов SSMA на SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
  
