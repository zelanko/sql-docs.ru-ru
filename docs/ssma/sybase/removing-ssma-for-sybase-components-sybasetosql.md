---
title: Удаление SSMA для Sybase компонентов (SybaseToSQL) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: aec09593-17d9-4ec2-ac56-3cd8851406fd
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d59d3d18b4eb5b5ec81cb12422cc16cf64592731
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="removing-ssma-for-sybase-components-sybasetosql"></a>Удаление SSMA для Sybase компонентов (SybaseToSQL)
После завершения миграции баз данных из Sybase адаптивной Server Enterprise (ASE) для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], может потребоваться удалить компоненты SSMA. Клиентские компоненты можно удалить в любое время, но не рекомендуется удалять пакет расширения из [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Если вы уверены, что перенесенной базы данных больше не использовать функции в **ssma_syb** схему **sysdb** базы данных.  
  
## <a name="uninstalling-the-ssma-for-sybase-client"></a>При удалении SSMA для Sybase клиента  
SSMA можно удалить с помощью **Установка и удаление программ**.  
  
**Чтобы удалить SSMA**  
  
1.  В панели управления откройте **Установка и удаление программ**.  
  
2.  Выберите **Microsoft SQL Server Migration Assistant для Sybase**, а затем нажмите кнопку **удалить**.  
  
3.  Чтобы подтвердить, что вы хотите удалить SSMA, щелкните **Да**.  
  
## <a name="uninstalling-the-extension-pack"></a>Удаление пакета расширения  
Если вы уверены, перенесенных баз данных не следует использовать объекты в **sysdb.ssma_syb** схемы, можно удалить пакет расширения с помощью **Установка и удаление программ**.  
  
Чтобы удалить пакет расширения  
  
1.  В панели управления откройте **Установка и удаление программ**.  
  
2.  Выберите **Microsoft SQL Server Migration Assistant для Sybase пакета расширения**, а затем нажмите кнопку **удалить**.  
  
3.  Чтобы подтвердить удаление пакета расширения, нажмите кнопку **Да**.  
  
4.  В экземплярах с страницы скриптов базы данных программы, нажмите кнопку **Далее**.  
  
5.  На странице Параметры подключения, выберите метод проверки подлинности и нажмите кнопку **Далее**.  
  
    Проверка подлинности Windows будет использовать учетные данные Windows для входа на экземпляр SQL Server. При выборе проверки подлинности SQL Server, необходимо ввести имя входа SQL Server и пароль.  
  
6.  На странице завершить операцию, нажмите кнопку **ОК**.  
  
7.  На странице «Готово», нажмите кнопку **выхода**.  
  
После удаления, можно проверить, **sysdb.ssma_syb** схемы и весь **sysdb** базы данных, была удалена с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. Тем не менее, если вы используете другие продукты SSMA, она также использует **sysdb** базы данных. Если база данных существует, и вы уверены, что нет других баз данных ссылок на объекты в этой базе данных, можно отсоединить базы данных.  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для клиента Sybase &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)  
[Установка компонентов SSMA на SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
  
