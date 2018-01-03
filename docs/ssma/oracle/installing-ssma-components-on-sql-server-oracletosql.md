---
title: "Установка компонентов SSMA на SQL Server (OracleToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Installign the Extension Pack
- SQL Server Database Objects
ms.assetid: 33070e5f-4e39-4b70-ae81-b8af6e4983c5
caps.latest.revision: "7"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 76880266efb8c38bffdaa4223e49822c6d3b0778
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="installing-ssma-components-on-sql-server-oracletosql"></a>Установка компонентов SSMA на SQL Server (OracleToSQL)
Помимо установки SSMA, необходимо установить компоненты на компьютере, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Эти компоненты включают пакет расширения SSMA, поддерживающей переноса данных и поставщики Oracle, чтобы включить возможность подключения сервера к серверу.  
  
## <a name="ssma-for-oracle-extension-pack"></a>SSMA для пакета расширения Oracle  
Пакет расширения SSMA добавляет баз данных, **sysdb** и **ssmatesterdb**, для указанного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Базы данных **sysdb** содержит таблицы и хранимые процедуры, необходимые для переноса данных и определяемые пользователем функции, позволяющие воссоздавать Oracle системные функции. **Ssmatesterdb** база данных содержит таблицы и процедур, необходимых для тест-инженер компонента.  
  
Кроме того, при переносе данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], создает SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] заданий агента, когда модуль переноса данных стороне сервера используется для переноса данных.  
  
### <a name="prerequisites"></a>предварительные требования  
Перед установкой SSMA для компонентов сервера Oracle на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], убедитесь в том, что система соответствует следующим требованиям:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]установлен экземпляр. SSMA не поддерживает SQL Server 2008 Express Edition.  
  
-   Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.  
  
-   Поставщик клиента Oracle или поставщик OLE DB для Oracle и возможность подключения к базе данных Oracle, которые требуется перенести. Поставщики можно установить с установочного носителя Oracle или Oracle веб-сайта.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Во время установки, должна быть запущена служба браузера. Эти сведения используются для заполнения списка экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] в мастере установки. Вы можете отключить [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] служба браузера после установки.  
  
    > [!NOTE]  
    > Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] запущена служба браузера, но по-прежнему отсутствует список экземпляров в программе установки, необходимо разблокировать порт UDP 1434. Можно использовать для временного разблокировать порт брандмауэра Windows, или можно временно отключить брандмауэр Windows. Кроме того, может потребоваться временно отключить антивирусное программное обеспечение. Не забудьте включить брандмауэров и антивирусного программного обеспечения после установки.  
  
### <a name="installing-the-extension-pack"></a>Установка пакета расширения  
Пакет расширения можно установить любое время, прежде чем переносить данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
> [!IMPORTANT]  
> Чтобы установить пакет расширения, необходимо быть членом **sysadmin** роли сервера на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
**Чтобы установить пакет расширения**  
  
1.  Если вы еще не сделано, извлеките все файлы из SSMA ZIP-файла.  
  
    В зависимости от версии WinZip, у вас есть, можно либо дважды щелкните файл, или щелкните правой кнопкой мыши файл и выберите **извлечь все** или **открыт в WinZip**. Следуйте инструкциям в пользовательском интерфейсе WinZip, чтобы извлечь файлы.  
  
2.  Скопируйте SSMA для расширения пакета Oracle. *n*. Install.exe, где  *n*  — номер сборки, на компьютер, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
3.  Дважды щелкните SSMA для расширения пакета Oracle. *n*. Install.exe.  
  
4.  На странице приветствия нажмите кнопку **Далее**.  
  
5.  На странице Лицензионное соглашение прочитайте лицензионное соглашение. Если вы согласны, установите **я принимаю условия лицензионного соглашения** флажок и нажмите кнопку **Далее**.  
  
6.  На странице Выбор типа установки щелкните **обычные**.  
  
7.  На странице готовности к установке, нажмите кнопку **установить**.  
  
8.  На завершено странице первый шаг установки, нажмите кнопку **Далее**.  
  
    Появится новое диалоговое окно, в котором можно выбрать экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] для установки пакета расширения.  
  
9. Выберите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] где вы будет перенос схемы Oracle, а затем нажмите кнопку **Далее**.  
  
    Экземпляр по умолчанию имеет имя, совпадающее с именем компьютера. Именованные экземпляры будут следовать обратную косую черту и имя экземпляра.  
  
10. На странице «соединение» выберите метод проверки подлинности и нажмите кнопку **Далее**.  
  
    Проверка подлинности Windows будет использовать учетные данные Windows для входа на экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. При выборе [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] проверки подлинности, необходимо ввести [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] имя входа и пароль.  
  
11. На следующей странице выберите **установки базы данных программы**  *n* , где  *n*  номер версии, а затем нажмите кнопку **Далее**.  
  
    **Sysdb** база данных создается и определяемые пользователем функции и хранимые процедуры создаются в этой базе данных.  
  
    Если **установки базы данных тест-инженер** флажок тест-инженер **ssmatesterdb** будет создана база данных.  
  
12. Чтобы установить эти программы на другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]выберите **Да**и нажмите кнопку **Далее**. Чтобы завершить работу мастера, нажмите кнопку **нет**.  
  
13. В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] или с помощью программы sqlcmd, запустите следующий сценарий, чтобы включить CLR:  
  
    ```  
    sp_configure 'clr enabled', 1  
    GO  
    RECONFIGURE  
    GO  
    ```  
    Если среда CLR не включена, появится следующая ошибка при подключении SSMA для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]:  
  
    SSMA не удалось получить сведения о версии сборки пакета расширений. Переустановите пакет расширения на сервере базы данных.  
  
### <a name="sql-server-database-objects"></a>Объекты базы данных SQL Server  
После установки пакета расширения, вы будете см. в разделе **ssma_oracle.bcp_migration_packages** таблицы, **ssma_oracle.db_storage** таблицы и **ssma_oracle.db_error_list** в таблицу **sysdb** базы данных. Вы также увидите множество хранимых процедур и определяемых пользователем функций в **ssma_oracle** схемы.  
  
Каждый раз при переносе данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], создает SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] задания агента. Эти задания называются **ssma_oracle данных миграции пакета {GUID}**и отображаются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] узел агента [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] в папку «задания».  
  
## <a name="see-also"></a>См. также:  
[Установка SSMA для клиента Oracle &#40; OracleToSQL &#41;](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[Миграция баз данных Oracle в SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
