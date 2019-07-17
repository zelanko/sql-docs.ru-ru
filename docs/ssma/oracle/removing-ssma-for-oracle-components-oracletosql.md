---
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
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 0434f88c46d14672c84f5f7939488a827b229e27
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68266563"
---
# <a name="removing-ssma--for-oracle-components-oracletosql"></a>Удаление компонентов SSMA для Oracle (OracleToSQL)
После завершения миграции баз данных Oracle для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], может потребоваться удаление компонентов SSMA. Клиентские компоненты можно удалить в любое время. Тем не менее, не рекомендуется удалять пакет расширений из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перенесенных баз данных больше не использовать функции в **ssma_oracle** схему **sysdb** базы данных.  
  
## <a name="uninstalling-the-ssma-for-oracle-client"></a>При удалении SSMA для клиента Oracle  
SSMA можно удалить с помощью **Установка и удаление программ**.  
  
**Чтобы удалить SSMA**  
  
1.  В панели управления откройте **Установка и удаление программ**.  
  
2.  Выберите  **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant для Oracle**, а затем нажмите кнопку **удалить**.  
  
3.  Чтобы убедиться, что вы хотите удалить SSMA, щелкните **Да**.  
  
## <a name="uninstalling-the-extension-pack"></a>Удаление пакета расширения  
Если вы уверены, перенесенных баз данных не следует использовать объекты в **sysdb.ssma_oracle** схемы, можно удалить пакет расширений с помощью **Установка и удаление программ**.  
  
**Удалить расширение пакета**  
  
1.  В панели управления откройте **Установка и удаление программ**.  
  
2.  Выберите **Microsoft SQL Server Migration Assistant для Oracle Extension Pack**, а затем нажмите кнопку **удалить**.  
  
3.  Чтобы подтвердить, что вы хотите удалить пакет расширений, щелкните **Да**.  
  
4.  В экземплярах с страницы скрипты базы данных программы, выберите экземпляр и нажмите кнопку **Далее**.  
  
5.  На странице Параметры подключения, выберите метод проверки подлинности и нажмите кнопку **Далее**.  
  
    Проверка подлинности Windows будет использовать учетные данные Windows для входа на экземпляр объекта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При выборе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности, необходимо ввести [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа и пароль.  
  
6.  На странице завершить операцию, нажмите кнопку **ОК**.  
  
7.  На странице "Готово", нажмите кнопку **выхода**.  
  
После удаления, можно убедиться, что объекты в **sysdb.ssma_oracle** схемы и, возможно, всю **sysdb** базы данных, был удален с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Тем не менее, если вы используете другие продукты SSMA, они также используют **sysdb** базы данных. Если база данных существует, и вы уверены, что нет других баз данных ссылок на объекты в этой базе данных, можно отсоединить базу данных.  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для клиента Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[Установка компонентов SSMA в SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
  
