---
title: Удаление компонентов Sybase (SybaseToSQL) SSMA для | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: aec09593-17d9-4ec2-ac56-3cd8851406fd
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: b3cebc9bb82778390716212fd3b5ae1bf800d3d3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62667938"
---
# <a name="removing-ssma-for-sybase-components-sybasetosql"></a>Удаление компонентов SSMA для Sybase (SybaseToSQL)
После завершения миграции баз данных из Sybase Adaptive Server Enterprise (ASE) для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], может потребоваться удаление компонентов SSMA. Клиентские компоненты можно удалить в любое время, но не рекомендуется удалять пакет расширений из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Если нет уверенности, что перенесенных баз данных больше не использовать функции в **ssma_syb** схему **sysdb** базы данных.  
  
## <a name="uninstalling-the-ssma-for-sybase-client"></a>Удаление SSMA для Sybase клиента  
SSMA можно удалить с помощью **Установка и удаление программ**.  
  
**Чтобы удалить SSMA**  
  
1.  В панели управления откройте **Установка и удаление программ**.  
  
2.  Выберите **Microsoft SQL Server Migration Assistant для Sybase**, а затем нажмите кнопку **удалить**.  
  
3.  Чтобы убедиться, что вы хотите удалить SSMA, щелкните **Да**.  
  
## <a name="uninstalling-the-extension-pack"></a>Удаление пакета расширения  
Если вы уверены, перенесенных баз данных не следует использовать объекты в **sysdb.ssma_syb** схемы, можно удалить пакет расширений с помощью **Установка и удаление программ**.  
  
Удалить расширение пакета  
  
1.  В панели управления откройте **Установка и удаление программ**.  
  
2.  Выберите **Microsoft SQL Server Migration Assistant для Sybase Extension Pack**, а затем нажмите кнопку **удалить**.  
  
3.  Чтобы подтвердить, что вы хотите удалить пакет расширений, щелкните **Да**.  
  
4.  В экземплярах с страницы скрипты базы данных служебных программ, нажмите кнопку **Далее**.  
  
5.  На странице Параметры подключения, выберите метод проверки подлинности и нажмите кнопку **Далее**.  
  
    Проверка подлинности Windows будет использовать учетные данные Windows для входа на экземпляр SQL Server. Если выбрана проверка подлинности SQL Server, необходимо ввести имя входа SQL Server и пароль.  
  
6.  На странице завершить операцию, нажмите кнопку **ОК**.  
  
7.  На странице "Готово", нажмите кнопку **выхода**.  
  
После удаления, это можно проверить, **sysdb.ssma_syb** схемы и, возможно, всю **sysdb** базы данных, был удален с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Тем не менее, если вы используете другие продукты SSMA, они также используют **sysdb** базы данных. Если база данных существует, и вы уверены, что нет других баз данных ссылок на объекты в этой базе данных, можно отсоединить базу данных.  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для Sybase клиента &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)  
[Установка компонентов SSMA в SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
  
