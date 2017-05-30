---
title: "Расположение файлов для экземпляров по умолчанию и именованных экземпляров SQL Server | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 463c570e-9f75-4653-b3b8-4d61753b0013
caps.latest.revision: 16
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e36929e0633942ab786178a46214c8507c9a65bc
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="file-locations-for-default-and-named-instances-of-sql-server"></a>Расположение файлов для экземпляра по умолчанию и именованных экземпляров SQL Server
  Установка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] состоит из одного или нескольких отдельных экземпляров. Как экземпляр по умолчанию, так и именованный экземпляр имеет собственный набор программных файлов и файлов данных, а также набор общих файлов, используемых всеми экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , установленными на компьютере.  
  
 Для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , включающего [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], каждый компонент имеет полный набор файлов данных и исполняемых файлов, а также общие файлы, используемые всеми компонентами.  
  
 Чтобы изолировать друг от друга папки установки, формируется уникальный идентификатор экземпляра для каждого из компонентов экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Программные файлы и файлы данных не могут быть установлены на съемном диске, в файловой системе со сжатием данных, в каталоге расположения системных файлов, а также на общих дисках экземпляра отказоустойчивого кластера.  
>  
>  Может потребоваться настроить программное обеспечение, например антивирусное и антишпионское приложения, чтобы исключить из проверки типы файлов и папки SQL Server. Дополнительные сведения см. в этой статье: [Антивирусное программное обеспечение на компьютерах, где выполняется SQL Server](https://support.microsoft.com/kb/309422).
> 
>  Системные базы данных (Master, Model, MSDB и TempDB) и пользовательские базы данных компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] можно установить с использованием протокола SMB в качестве хранилища файлового сервера Server Message Block (SMB). Это относится как к изолированному варианту установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и к установке кластеров отработки отказа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе [Install SQL Server with SMB Fileshare as a Storage Option](../../database-engine/install-windows/install-sql-server-with-smb-fileshare-as-a-storage-option.md).  
>   
>  Не удаляйте следующие каталоги или их содержимое: Binn, Data, Ftdata, HTML или 1033. При необходимости можно удалить другие каталоги, однако возможно, что не удастся вернуть утраченную функциональность или восстановить потерянные данные без удаления и повторной установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не удаляйте и не изменяйте HTM-файлы в каталоге HTML. Они необходимы для правильной работы средств [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="shared-files-for-all-instances-of-includessnoversionincludesssnoversion-mdmd"></a>Общие файлы для всех экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Общие файлы, используемые всеми экземплярами на одном компьютере, устанавливаются в папке [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)], где параметр \<*диск*> означает имя диска, на котором устанавливаются компоненты. По умолчанию диск С.  
  
## <a name="file-locations-and-registry-mapping"></a>Расположение файлов и сопоставление данных реестра  
 Во время установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для каждого компонента сервера создается идентификатор экземпляра. В этой версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сервер состоит из компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 Идентификатор экземпляра по умолчанию указывается в следующем формате.  
  
-   Для компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]— MSSQL, за которым следуют основной номер версии, символ подчеркивания и дополнительный номер версии (если применимо), затем точка и имя экземпляра.  
  
-   Для служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]— MSAS, за которым следуют основной номер версии, символ подчеркивания и дополнительный номер версии (если применимо), затем точка и имя экземпляра.  
  
-   Для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]— MSRS, за которым следуют основной номер версии, символ подчеркивания и дополнительный номер версии (если применимо), затем точка и имя экземпляра.  
  
 Ниже приведены примеры идентификаторов экземпляров по умолчанию для данной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   MSSQL13.MSSQLSERVER — экземпляр по умолчанию [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   MSAS13.MSSQLSERVER — экземпляр по умолчанию [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)].  
  
-   MSSQL13.MyInstance — именованный экземпляр [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с именем MyInstance.  
  
 Именованный экземпляр [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , в состав которого входит компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] и службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], имеет имя «MyInstance» и устанавливается каталоге по умолчанию, имеет следующую структуру каталогов.  
  
-   C:\Program Files\Microsoft SQL Server\MSSQL13.MyInstance\  
  
-   C:\Program Files\Microsoft SQL Server\MSAS13.MyInstance\  
  
 В качестве идентификатора экземпляра может быть указано любое значение, следует только избегать применения специальных символов и зарезервированных ключевых слов.  
  
 Идентификатор экземпляра, отличный от заданного по умолчанию, можно указать во время установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если пользователь изменит каталог установки по умолчанию, вместо \<Program Files>\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется \<указанный_пользователем_путь>\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Следует заметить, что идентификаторы экземпляров, начинающиеся с символа подчеркивания (_) или содержащие символ решетки (#) или знак доллара ($), не поддерживаются.  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и клиентские компоненты не привязаны к экземпляру, поэтому им не присваивается идентификатор экземпляра. По умолчанию компоненты, не привязанные к экземпляру, устанавливаются в один каталог: [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]. Изменение пути установки для одного компонента приводит к его изменению и для всех остальных компонентов. При последующих установках компоненты, не зависящие от экземпляра, устанавливаются в каталог исходной установки.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] являются единственным компонентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который поддерживает переименование экземпляра после установки. При переименовании экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] его идентификатор экземпляра не изменится. После переименования экземпляра в каталогах и разделах реестра по-прежнему используется идентификатор экземпляра, созданный во время установки.  
  
 В разделе реестра HKLM\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\<*идентификатор_экземпляра*> создается куст для компонентов, привязанных к экземпляру. Например:  
  
-   HKLM\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.MyInstance  
  
-   HKLM\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSAS13.MyInstance  
  
-   HKLM\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSRS13.MyInstance  
  
 В реестре также хранится сопоставление идентификаторов экземпляров с именами экземпляров. Сопоставление идентификатора экземпляра с именем экземпляра осуществляется следующим образом:  
  
-   [HKEY_LOCAL_MACHINE\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\имена экземпляров\SQL] "InstanceName"="MSSQL13"  
  
-   [HKEY_LOCAL_MACHINE\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\имена экземпляров\OLAP] "InstanceName"="MSAS13"  
  
-   [HKEY_LOCAL_MACHINE\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\имена экземпляров\RS] "InstanceName"="MSRS13"  
  
## <a name="specifying-file-paths"></a>Указание путей к файлам  
 В ходе установки вы можете изменить путь установки для следующих компонентов:  
  
 Путь установки отображается в программе установки только для компонентов с пользовательской целевой папкой.  
  
|Компонент|Путь по умолчанию|Настраиваемый или фиксированный путь|  
|---------------|------------------|--------------------------------|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] компоненты сервера|\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.\<идентификатор_экземпляра>\|Настраиваемый|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] файлы данных|\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.\<идентификатор_экземпляра>\|Настраиваемый|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] сервер|\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSAS13.\<идентификатор_экземпляра>\|Настраиваемый|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] файлы данных|\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSAS13.\<идентификатор_экземпляра>\|Настраиваемый|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] сервер отчетов|\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSRS13.\<идентификатор_экземпляра>\Reporting Services\ReportServer\Bin\|Настраиваемый|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] диспетчер отчетов|\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSRS13.\<идентификатор_экземпляра\Reporting Services\ReportManager\|Фиксированный путь|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|\<каталог установки>\130\DTS\|Настраиваемый*|  
|Клиентские компоненты (за исключением bcp.exe и sqlcmd.exe)|\<каталог установки>\130\Tools\|Настраиваемый*|  
|Клиентские компоненты (bcp.exe и sqlcmd.exe)|\<Каталог установки>\Client SDK\ODBC\110\Tools\Binn|Фиксированный путь|  
|Объекты COM для репликации и размещения на сервере|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]COM\\**|Фиксированный путь|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] библиотеки DLL служб для механизмов преобразования данных в реальном режиме времени и конвейерного преобразования данных и программа командной строки **dtexec**|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]DTS\Binn|Фиксированный путь|  
|Библиотеки DLL, которые обеспечивают управляемое соединение, поддерживаемое для служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]DTS\Connections|Фиксированный путь|  
|Библиотеки DLL для каждого типа перечислителей, которые поддерживают службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]DTS\ForEachEnumerators|Фиксированный путь|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , поставщики инструментария WMI|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]Shared\|Фиксированный путь|  
|Компоненты, которые разделены между всеми экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]Shared\|Фиксированный путь|  
  
 **\*\* Примечание по безопасности. \*\*** Убедитесь, чтобы папка \Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\ защищена ограниченными разрешениями.  
  
 Обратите внимание, что диск по умолчанию для расположений файлов — *systemdrive*, обычно это диск C. Пути установки вложенных компонентов определяются путем установки родительского компонента.  
  
 * Используется общий путь установки для компонентов [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и клиентских компонентов. Изменение пути установки для одного компонента влечет изменение пути для других компонентов. При последующих установках компоненты устанавливаются в расположение исходной установки.  
  
 ** Этот каталог используется всеми экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на компьютере. При применении обновления к любому из экземпляров на компьютере все файловые изменения коснутся каждого из них. При добавлении компонентов в существующую конфигурацию невозможно ни изменить расположение ранее установленного компонента, ни указать расположение нового. Необходимо либо установить дополнительные компоненты в каталоги, созданные программой установки, либо удалить продукт и установить его заново.  
  
> [!NOTE]  
>  Для кластеризованных конфигураций необходимо выбрать локальный диск, доступный на всех узлах кластера.  
  
 При задании пути установки во время установки компонентов сервера или файлов данных программа установки использует идентификатор экземпляра в дополнение к заданному положению для программ и файлов данных. Программа установки не пользуется идентификаторами экземпляров для средств и других общих файлов. Идентификатор экземпляра также не используется для программ и файлов данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , но используется для репозитория служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 При указании пути установки для компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] программа установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует этот путь в качестве корневого каталога этой установки для всех папок, относящихся к экземпляру, включая файлы данных SQL. Если в этом случае указать в качестве корневого каталога "C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.\<имя_экземпляра>\MSSQL\\", то каталоги, относящиеся к данному экземпляру, будут добавлены в конец этого пути.  
  
 Поэтому при использовании функции обновления USESYSDB в мастере установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (режим установки с пользовательским интерфейсом) можно попасть в ситуацию, когда продукт окажется установленным в рекурсивной структуре папок. Например, \<*SQLProgramFiles*>\MSSQL13\MSSQL\MSSQL10_50\MSSQL\Data\\. Поэтому при использовании функции USESYSDB вместо компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] необходимо указывать путь установки файлов данных SQL.  
  
> [!NOTE]  
>  Обычно файлы данных можно найти в дочернем каталоге с именем Data. Например, если при обновлении вы укажете значение C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.\<имя_экземпляра\ в качестве корневого каталога данных для системных баз данных, файлы данных должны располагаться в каталоге C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL13.\<<имя_экземпляра\MSSQL\Data.  
  
## <a name="see-also"></a>См. также:  
 [Настройка ядра СУБД — каталоги данных](http://msdn.microsoft.com/library/9b1fa0fc-623b-479a-afc3-4f13bd850487)   
 [Настройка служб Analysis Services — каталоги данных](http://msdn.microsoft.com/library/ef732855-b7af-4f40-a619-5573c1c354bb)  
  
  
