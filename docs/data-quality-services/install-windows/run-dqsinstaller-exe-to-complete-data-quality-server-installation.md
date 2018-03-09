---
title: "Запуск файла DQSInstaller.exe для завершения установки сервера служб DQS | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: data-quality-services
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: sql
ms.technology: data-quality-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a8c96e0-1328-4f35-97fc-b6d9cb808bae
caps.latest.revision: "33"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: d6d14694ebc822f28c7765d1ed7235b77e4db06c
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/19/2018
---
# <a name="run-dqsinstallerexe-to-complete-data-quality-server-installation"></a>Запуск файла DQSInstaller.exe для завершения установки сервера служб DQS
  Чтобы завершить установку сервера [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] , необходимо запустить файл DQSInstaller.exe после установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. В этом разделе описан запуск файла DQSInstaller.exe на экране **Пуск** или в меню **Пуск** , в проводнике Windows и из командной строки. Для запуска файла DQSInstaller.exe можно воспользоваться любым из этих способов.  
  
##  <a name="Prerequisites"></a> Предварительные требования  
  
-   Необходимо выбрать **Службы Data Quality Services** в разделе **Службы компонента Database Engine** на странице "Выбор компонентов" программы установки SQL Server и завершить установку SQL Server. Дополнительные сведения см. в разделе [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).  
  
-   Учетная запись пользователя Windows должна входить в предопределенную роль сервера sysadmin на экземпляре компонента SQL Server Database Engine.  
  
-   Необходимо выполнить вход от имени члена группы администраторов на компьютере, где запускается файл DQSInstaller.exe.  
  
##  <a name="WindowsExplorer"></a> Запуск файла DQSInstaller.exe с экрана «Пуск», из меню «Пуск» или из проводника Windows  
  
1.  Запустите файл DQSInstaller.exe на компьютере, где необходимо установить сервер [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)], одним из следующих способов.  
  
    -   **Экран запуска**: на экране **Пуск** нажмите кнопку **Программа установки Data Quality Server**  
  
    -   **Меню "Пуск"**: на панели задач нажмите кнопку **Пуск**, укажите **Все программы**и выберите [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]. В разделе [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]щелкните **Data Quality Services**и выберите **Программа установки Data Quality Server.**  
  
    -   **Проводник Windows**: найдите файл DQSInstaller.exe. Если был установлен экземпляр SQL Server по умолчанию, файл DQSInstaller.exe будет помещен в папку C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn. Дважды щелкните файл DQSInstaller.exe.  
  
2.  На экране откроется окно командной строки, в котором будет отображаться состояние установки. Обратите внимание на следующие три момента.  
  
    1.  Установщик создаст файл журнала установки DQS_install.log, в котором будут приведены сведения о действиях, выполненных после запуска файла DQSInstaller.exe. Если был установлен экземпляр SQL Server по умолчанию, файл DQS_install.log будет помещен в папку C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Log.  
  
    2.  Установщик использует для установки сервера [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]параметры сортировки сервера по умолчанию — SQL_Latin1_General_CP1_CI_AS.  
  
        > [!IMPORTANT]  
        >  Можно задать другие параметры сортировки сервера для установки [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] , но только в том случае, если файл DQSInstaller.exe был запущен из командной строки. Дополнительные сведения см. в разделе [Запуск DQSInstaller.exe из командной строки](#CommandPrompt) далее в этом разделе.  
  
    3.  Программа установки проверяет необходимость выполнения перезагрузки компьютера, если какие-либо обновления были недавно установлены. Если возникла необходимость выполнения перезагрузки, прекратите процесс установки и перезагрузите компьютер, а затем заново запустите файл DQSInstaller.exe. В том случае, если компьютер ожидает перезагрузки, рекомендуется прекратить процесс установки, перезагрузить компьютер, после чего заново запустить файл DQSInstaller.exe.  
  
3.  Откроется окно с запросом пароля для главного ключа базы данных. Главный ключ базы данных используется для шифрования ключей справочных служб данных стороннего поставщика, которые сохраняются в базе данных DQS_MAIN при последующей настройке поставщиков справочных данных в [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS).  
  
    > [!IMPORTANT]  
    >  Пароль должен состоять минимум из восьми символов и содержать символы как минимум трех из четырех категорий: прописные буквы английского алфавита (A, B, C,… Z), строчные буквы английского алфавита (a, b, c,… z), цифры (0, 1, 2,… 9) и специальные символы (~!@#$%^&*()_-+=|\\{}[]:;"'<>,.?/). Например, P@ssword. Если пароль не удовлетворяет этим требованиям, установщик попросит ввести другой пароль.  
  
4.  Введите пароль, подтвердите его, а затем нажмите клавишу ВВОД, чтобы продолжить установку.  
  
    > [!IMPORTANT]  
    >  Необходимо сохранить пароль, указанный для главного ключа базы данных, поскольку в будущем он потребуется при восстановлении баз данных служб DQS из резервной копии. Дополнительные сведения о создании резервной копии баз данных DQS см. в разделе [Резервное копирование и восстановление баз данных DQS](../../data-quality-services/backing-up-and-restoring-dqs-databases.md).  
  
5.  Если база данных служб Master Data Services находится на том же экземпляре SQL Server, что и сервер [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)], установщик создает пользователя, сопоставленного с именем входа служб Master Data Services, которому предоставляется роль dqs_administrator в базе данных DQS_MAIN. Сведения об установке служб Master Data Services и создании базы данных этих служб см. в разделе [Установка служб Master Data Services](../../master-data-services/install-windows/install-master-data-services.md).  
  
6.  После успешного завершения установки сообщение об этом появится на экране. Чтобы закрыть окно командной строки, нажмите любую кнопку.  
  
##  <a name="CommandPrompt"></a> Запуск DQSInstaller.exe из командной строки  
 Вы можете запустить файл DQSInstaller.exe из командной строки со следующими параметрами:  
  
|Параметр DQSInstaller.exe|Description|Образец синтаксиса|  
|--------------------------------|-----------------|-------------------|  
|-collation|Параметры сортировки сервера используются во время установки [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)].<br /><br /> Службы DQS поддерживают только параметры сортировки без учета регистра символов. Если указаны параметры сортировки с учетом регистра, то установщик попытается воспользоваться указанной версией параметров сортировки без учета регистра. Если для параметров сортировки отсутствует версия без учета регистра или они не поддерживаются SQL Server, процесс установки сервера [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] завершится ошибкой.<br /><br /> Если параметры сортировки сервера не указаны, используются параметры сортировки по умолчанию: SQL_Latin1_General_CP1_CI_AS.|`dqsinstaller.exe –collation <collation_name>`|  
|-upgradedlls|Пропускает повторное создание баз данных DQS (DQS_MAIN, DQS_PROJECTS и DQS_STAGING_DATA) и обновляет только сборки среды SQLCLR, используемые службами DQS в базе данных [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .<br /><br /> Дополнительные сведения см. в разделе [Обновление сборок SQLCLR после обновления .NET Framework](../../data-quality-services/install-windows/upgrade-sqlclr-assemblies-after-net-framework-update.md)|`dqsinstaller.exe -upgradedlls`|  
|-exportkbs|Экспорт всех баз знаний в файл резервной копии DQS (файл DQSB). Также необходимо указать полный путь и имя файла, в который будут экспортированы все базы знаний.<br /><br /> Дополнительные сведения см. в статье [Export and Import DQS Knowledge Bases Using DQSInstaller.exe](../../data-quality-services/install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md).|`dqsinstaller.exe –exportkbs <path><filename>`<br /><br /> Например: `dqsinstaller.exe –exportkbs c:\DQSBackup.dqsb`|  
|-importkbs|Импорт всех баз знаний из файла резервной копии DQS (файл DQSB) после завершения установки [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] . Также необходимо указать полный путь и имя файла, из которого будут импортированы все базы знаний.<br /><br /> Дополнительные сведения см. в статье [Экспорт и импорт баз знаний DQS с помощью DQSInstaller.exe](../../data-quality-services/install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md).|`dqsinstaller.exe –importkbs <path><filename>`<br /><br /> Например: `dqsinstaller.exe –importkbs c:\DQSBackup.dqsb`|  
|-upgrade|Обновляет схемы баз данных DQS. Этот параметр следует использовать после установки обновления SQL Server на ранее настроенном экземпляре служб DQS. Дополнительные сведения см. в разделе [Обновление схемы базы данных DQS после установки обновления SQL Server](../../data-quality-services/install-windows/upgrade-dqs-databases-schema-after-installing-sql-server-update.md).|`dqsinstaller.exe -upgrade`|  
|-uninstall|Удаляет [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] с текущего экземпляра SQL Server.<br /><br /> Также вы можете экспортировать все базы знаний из имеющейся установки Data Quality Server в файл резервной копии DQS (файл DQSB), а затем удалить Data Quality Server. Дополнительные сведения см. в статье [Экспорт и импорт баз знаний DQS с помощью DQSInstaller.exe](../../data-quality-services/install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md).<br /><br /> **\*\* Важно! \*\*** Если установить [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] из экземпляра SQL Server, используя параметр командной строки `–uninstall` , все объекты DQS в процессе удаления будут уничтожены. Удалять данные объекты вручную после удаления [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] не потребуется, как упоминалось в разделе [Удаление объектов служб Data Quality Services](../../sql-server/install/remove-data-quality-server-objects.md).|**Удаление только Data Quality Server**<br /><br /> `dqsinstaller.exe –uninstall`<br /><br /> **Экспорт всех баз знаний в файл и последующее удаление Data Quality Server**<br /><br /> `dqsinstaller.exe –uninstall <path><filename>`<br /><br /> Например: `dqsinstaller.exe –uninstall c:\DQSBackup.dqsb`|  
  
 **Запуск программы DQSInstaller.exe из командной строки**  
  
1.  Откройте командную строку.  
  
2.  В командной строке перейдите в папку, где находится файл DQSInstaller.exe. Если был установлен экземпляр SQL Server по умолчанию, файл DQSInstaller.exe будет помещен в папку C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn:  
  
    ```  
    cd C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn  
    ```  
  
3.  Запустите файл DQSInstaller.exe из командной строки со следующими параметрами или без них:  
  
    -   **Без параметров командной строки**: введите `dqsinstaller.exe`и нажмите клавишу ВВОД.  
  
    -   **С параметром командной строки**: введите необходимую команду, как указано в таблице выше, и нажмите клавишу ВВОД.  
  
4.  Необходимые действия выполняются исходя из указанной команды: Если выбрана установка сервера [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] без параметров командной строки, оставшиеся шаги установки будут аналогичны шагам 2–6 подраздела [Запуск файла DQSInstaller.exe с экрана "Пуск", из меню "Пуск" или из проводника Windows](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#WindowsExplorer).  
  
## <a name="next-steps"></a>Next Steps  
  
-   Предоставьте пользователям соответствующие роли DQS с учетом профиля их работы. См. раздел [Предоставление ролей DQS пользователям](../../data-quality-services/install-windows/grant-dqs-roles-to-users.md).  
  
-   Если к [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] будет осуществляться удаленный доступ клиента [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)], то с помощью диспетчера конфигурации SQL Server на этом компьютере следует включить протокол TCP/IP.  
  
-   Убедитесь, что исходные данные доступны для операций DQS и возможен экспорт обработанных данных в таблицу в базе данных. См. раздел [Предоставление доступа к данным для операций со службами DQS](../../data-quality-services/install-windows/access-data-for-the-dqs-operations.md).  
  
## <a name="see-also"></a>См. также:  
 [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)   
 [Обновление сборок SQLCLR после загрузки обновлений .NET Framework](../../data-quality-services/install-windows/upgrade-sqlclr-assemblies-after-net-framework-update.md)   
 [Экспорт и импорт баз знаний DQS с помощью DQSInstaller.exe](../../data-quality-services/install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md)  
  
  
