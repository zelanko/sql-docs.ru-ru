---
title: Установка компонентов SSMA в SQL Server (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Installign the Extension Pack
- SQL Server Database Objects
ms.assetid: 33070e5f-4e39-4b70-ae81-b8af6e4983c5
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 2041901a851ca755b1079535ccbf763472ec7bc4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47853362"
---
# <a name="installing-ssma-components-on-sql-server-oracletosql"></a>Установка компонентов SSMA в SQL Server (OracleToSQL)
Помимо установки SSMA, необходимо также установить компоненты на компьютере, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эти компоненты включают пакет расширений SSMA, которая поддерживает перенос данных и поставщики Oracle, чтобы обеспечить подключение между серверами.  
  
## <a name="ssma-for-oracle-extension-pack"></a>SSMA для Oracle Extension Pack  
Пакет расширений SSMA добавляет баз данных, **sysdb** и **ssmatesterdb**, для указанного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Базы данных **sysdb** содержит таблицы и хранимые процедуры, которые необходимы для переноса данных и определяемые пользователем функции, которые имитируют Oracle системные функции. **Ssmatesterdb** база данных содержит таблицы и процедуры, которые требуются в компоненте тест-инженер.  
  
Кроме того, при переносе данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], создает SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задания агента, когда модуль переноса данных на стороне сервера используется для переноса данных.  
  
### <a name="prerequisites"></a>предварительные требования  
Перед установкой SSMA для Oracle серверные компоненты на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], убедитесь, что система соответствует следующим требованиям:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлен экземпляр. SSMA не поддерживает SQL Server 2008 Express Edition.  
  
-   Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.  
  
-   Поставщик клиента Oracle или поставщик OLE DB для Oracle и подключение к базе данных Oracle, которые требуется перенести. Поставщики можно установить из установочного носителя Oracle или Oracle веб-сайта.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Во время установки, должна быть запущена служба браузера. Используется для заполнения списка экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в мастере установки. Вы можете отключить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] служба браузера после установки.  
  
    > [!NOTE]  
    > Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] служба браузера запущена, но вы по-прежнему не видите списка экземпляров в программе установки, необходимо разблокировать порт UDP 1434. Чтобы временно разблокировать порт можно использовать брандмауэр Windows, или можно временно отключить брандмауэр Windows. Кроме того, может потребоваться временно отключить антивирусную программу. Не забудьте включить брандмауэров и антивирусного программного обеспечения после установки.  
  
### <a name="installing-the-extension-pack"></a>Установка пакета расширения  
Пакет расширений можно установить любое время, прежде чем переносить данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
> Чтобы установить пакет расширения, необходимо быть членом **sysadmin** роли сервера на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Чтобы установить пакет расширений**  
  
1.  Если вы еще не сделали это, извлеките все файлы из SSMA ZIP-файла.  
  
    В зависимости от версии WinZip, у вас есть, вы можете дважды щелкните файл, или щелкните правой кнопкой мыши файл и выберите **извлечь все** или **открыт в WinZip**. Следуйте инструкциям в пользовательском интерфейсе WinZip, чтобы извлечь файлы.  
  
2.  Скопируйте SSMA для Oracle пакета расширения. *n*. Install.exe, где *n* — номер сборки, на компьютер, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3.  Дважды щелкните SSMA для Oracle пакета расширения. *n*. Install.exe.  
  
4.  На странице приветствия нажмите кнопку **Далее**.  
  
5.  На странице "лицензионное соглашение" Прочитайте лицензионное соглашение. Если вы согласны, установите **я принимаю условия лицензионного соглашения** флажок и нажмите кнопку **Далее**.  
  
6.  На странице "Выбор типа установки" нажмите кнопку **обычные**.  
  
7.  На странице готовности к установке, нажмите кнопку **установить**.  
  
8.  На Completed странице первый шаг установки, нажмите кнопку **Далее**.  
  
    Появится новое диалоговое окно, в котором можно выбрать экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для установки пакета расширения.  
  
9. Выберите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] где вам будет миграции схем Oracle, а затем нажмите кнопку **Далее**.  
  
    Экземпляр по умолчанию имеет имя, совпадающее с именем компьютера. Именованные экземпляры будут следовать обратную косую черту и имя экземпляра.  
  
10. На странице "Подключение", выберите метод проверки подлинности и нажмите кнопку **Далее**.  
  
    Проверка подлинности Windows будет использовать учетные данные Windows для входа на экземпляр объекта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При выборе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности, необходимо ввести [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа и пароль.  
  
11. На следующей странице выберите **установить базы данных служебных программ** *n*, где *n* — это номер версии, а затем нажмите кнопку **Далее**.  
  
    **Sysdb** создания базы данных и определяемые пользователем функции и хранимые процедуры создаются в этой базе данных.  
  
    Если **установить базы данных тест-инженер** флажок тест-инженер **ssmatesterdb** будет создана база данных.  
  
12. Чтобы установить служебные программы с другим экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]выберите **Да**и нажмите кнопку **Далее**. Чтобы выйти из мастера, нажмите кнопку **нет**.  
  
13. В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью программы sqlcmd, запустите следующий сценарий, чтобы включить CLR:  
  
    ```  
    sp_configure 'clr enabled', 1  
    GO  
    RECONFIGURE  
    GO  
    ```  
    Если среда CLR не включена, вы получите следующую ошибку, когда SSMA подключается к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    SSMA не удалось получить сведения о версии сборки пакета расширений. Переустановите пакет расширения на сервере базы данных.  
  
### <a name="sql-server-database-objects"></a>Объекты базы данных SQL Server  
После установки пакета расширения, вы будете см. в разделе **ssma_oracle.bcp_migration_packages** таблицы, **ssma_oracle.db_storage** таблицы и **ssma_oracle.db_error_list** в таблицу **sysdb** базы данных. Вы также увидите многие хранимые процедуры и определяемые пользователем функции в **ssma_oracle** схемы.  
  
Каждый раз, переносить данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], создает SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задания агента. Эти задания называются **ssma_oracle данных миграции пакета {GUID}** и отображаются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] узел агента [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] в папку «задания».  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для клиента Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[Переход с Oracle баз данных в SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
