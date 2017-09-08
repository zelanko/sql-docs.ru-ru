---
title: "Установка компонентов SSMA на SQL Server (MySQLToSql) | Документы Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- SSMA extension pack, Installation
ms.assetid: 6772d0c5-258f-4d7b-afb0-b5f810e71af1
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9544fb62402871b9a93284df88e0082f62fec582
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="installing-ssma-components-on-sql-server-mysqltosql"></a>Установка компонентов SSMA на SQL Server (MySQLToSql)
Помимо установки SSMA, необходимо установить компоненты на компьютере, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Эти компоненты включают пакет расширения SSMA, поддерживающей переноса данных и поставщики MySQL, чтобы включить возможность подключения сервера к серверу.  
  
## <a name="ssma-for-mysql-extension-pack"></a>SSMA для пакета расширение MySQL  
Пакет расширения SSMA добавляет базу данных, **sysdb**, для указанного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Эта база данных содержит таблицы и хранимые процедуры, необходимые для переноса данных.  
  
Кроме того, при переносе данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], создает SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] задания агента, когда модуль переноса данных стороне сервера используется для переноса данных.  
  
### <a name="prerequisites"></a>Предварительные требования  
Перед установкой SSMA для компонентов сервера MySQL на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], убедитесь в том, что компьютер соответствует следующим требованиям:  
  
-   Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.  
  
-   Поставщик клиента MySQL и подключение к базе данных MySQL, которые требуется перенести. Поставщики можно установить из установочного носителя MySQL или MySQL веб-сайта.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Во время установки, должна быть запущена служба браузера. Эти сведения используются для заполнения списка экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] в мастере установки. Вы можете отключить [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] служба браузера после установки.  
  
    > [!NOTE]  
    > Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] запущена служба браузера, но по-прежнему отсутствует список экземпляров в программе установки, необходимо разблокировать порт UDP 1434. Можно использовать для временного разблокировать порт брандмауэра Windows, или можно временно отключить брандмауэр Windows. Кроме того, может потребоваться временно отключить антивирусное программное обеспечение. Не забудьте включить брандмауэров и антивирусного программного обеспечения после установки.  
  
### <a name="installing-the-extension-pack"></a>Установка пакета расширения  
Пакет расширения можно установить любое время, прежде чем переносить данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
> [!IMPORTANT]  
> Чтобы установить пакет расширения, необходимо быть членом **sysadmin** роли сервера на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
**Чтобы установить пакет расширения**  
  
1.  Скопируйте SSMA для пакета расширения MySQL. *n*. Install.exe, где  *n*  — номер сборки, на компьютер, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
2.  Дважды щелкните SSMA для пакета расширения MySQL. *n*. Install.exe.  
  
3.  В диалоговом окне приветствия щелкните **Далее**.  
  
4.  В диалоговом окне лицензионного соглашения прочтите лицензионное соглашение. Если вы согласны, установите **я принимаю условия лицензионного соглашения** флажок и нажмите кнопку **Далее**.  
  
5.  В диалоговом окне Выбор типа установки щелкните **обычные**.  
  
6.  На все готово для установки диалоговое окно, нажмите кнопку **установить**.  
  
7.  На завершено диалоговым окном первого шага установки, нажмите кнопку **Далее**.  
  
    Появится новое диалоговое окно, в котором можно выбрать экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] для установки пакета расширения.  
  
8.  Выберите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] где вы будет перенос схемы MySQL, а затем нажмите кнопку **Далее**.  
  
    Экземпляр по умолчанию имеет имя, совпадающее с именем компьютера. Именованные экземпляры будут следовать обратную косую черту и имя экземпляра.  
  
9. В диалоговом окне подключения, выберите метод проверки подлинности и нажмите кнопку **Далее**.  
  
    Проверка подлинности Windows будет использовать учетные данные Windows для входа на экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. При выборе [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] проверки подлинности, необходимо ввести [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] имя входа и пароль.  
  
10. В следующем диалоговом выберите **установки базы данных программы**  *n* , где  *n*  номер версии, а затем нажмите кнопку **Далее**.  
  
    **Sysdb** база данных создается с таблицами, в этой базе данных создаются хранимые процедуры, необходимые для переноса данных (с помощью модуль переноса данных стороны сервера).  
  
11. Чтобы установить эти программы на другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]выберите **Да**и нажмите кнопку **Далее**. Чтобы завершить работу мастера, нажмите кнопку **нет**.  
  
## <a name="see-also"></a>См. также:  
[Установка SSMA для клиента MySQL &#40; MySQLToSQL &#41;](../../ssma/mysql/installing-ssma-for-mysql-client-mysqltosql.md)  
[Миграция баз данных MySQL в SQL Server — база данных Azure SQL &#40; MySQLToSql &#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  

