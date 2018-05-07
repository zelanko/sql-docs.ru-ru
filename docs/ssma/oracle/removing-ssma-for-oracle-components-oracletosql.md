---
title: Удаление SSMA для компонентов Oracle (OracleToSQL) | Документы Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Uninstalling the Extension Pack
ms.assetid: 8b527a56-4e52-487a-9ac9-2320388e6d7d
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: dc119244850dd7e7925b9f858fe8ea5cbf28ecda
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="removing-ssma--for-oracle-components-oracletosql"></a>Удаление SSMA для компонентов Oracle (OracleToSQL)
После завершения миграции баз данных Oracle, чтобы [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], может потребоваться удалить компоненты SSMA. Клиентские компоненты можно удалить в любое время. Однако не рекомендуется удалять пакет расширения из [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Если перенесенной базы данных больше не использовать функции в **ssma_oracle** схему **sysdb** базы данных.  
  
## <a name="uninstalling-the-ssma-for-oracle-client"></a>При удалении SSMA для клиента Oracle  
SSMA можно удалить с помощью **Установка и удаление программ**.  
  
**Чтобы удалить SSMA**  
  
1.  В панели управления откройте **Установка и удаление программ**.  
  
2.  Выберите  **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant для Oracle**, а затем нажмите кнопку **удалить**.  
  
3.  Чтобы подтвердить, что вы хотите удалить SSMA, щелкните **Да**.  
  
## <a name="uninstalling-the-extension-pack"></a>Удаление пакета расширения  
Если вы уверены, перенесенных баз данных не следует использовать объекты в **sysdb.ssma_oracle** схемы, можно удалить пакет расширения с помощью **Установка и удаление программ**.  
  
**Чтобы удалить пакет расширения**  
  
1.  В панели управления откройте **Установка и удаление программ**.  
  
2.  Выберите **Microsoft SQL Server Migration Assistant для Oracle пакета расширения**, а затем нажмите кнопку **удалить**.  
  
3.  Чтобы подтвердить удаление пакета расширения, нажмите кнопку **Да**.  
  
4.  В экземплярах с страницы скриптов базы данных программы, выберите экземпляр и нажмите кнопку **Далее**.  
  
5.  На странице Параметры подключения, выберите метод проверки подлинности и нажмите кнопку **Далее**.  
  
    Проверка подлинности Windows будет использовать учетные данные Windows для входа на экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. При выборе [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] проверки подлинности, необходимо ввести [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] имя входа и пароль.  
  
6.  На странице завершить операцию, нажмите кнопку **ОК**.  
  
7.  На странице «Готово», нажмите кнопку **выхода**.  
  
После удаления, можно убедиться, что объекты, в **sysdb.ssma_oracle** схемы и весь **sysdb** базы данных, была удалена с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. Тем не менее, если вы используете другие продукты SSMA, она также использует **sysdb** базы данных. Если база данных существует, и вы уверены, что нет других баз данных ссылок на объекты в этой базе данных, можно отсоединить базы данных.  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для клиента Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[Установка компонентов SSMA на SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
  
