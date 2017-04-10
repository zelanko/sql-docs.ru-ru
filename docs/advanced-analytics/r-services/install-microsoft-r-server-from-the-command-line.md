---
title: "Установка Microsoft R Server из командной строки | Microsoft Docs"
ms.custom: ""
ms.date: "01/19/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb4446ba-e9ce-4b93-9854-5e8a58507da0
caps.latest.revision: 4
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 3
---
# Установка Microsoft R Server из командной строки
    
Microsoft R Server можно установить из командной строки с помощью средств написания скриптов, предоставляемых программой установки SQL Server. 

- Для **автоматической** установки требуется указать расположение программы установки и использовать аргументы, чтобы указать устанавливаемые компоненты. 
- Для **тихой** установки укажите те же самые аргументы, добавив параметр **/q**. При этом никакие запросы не выводятся и вмешательство пользователя не требуется. Однако при отсутствии любого из обязательных аргументов программа установки завершится ошибкой.

Дополнительные сведения см. в статье [Установка SQL Server 2016 из командной строки](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).

## <a name="perform-a-command-line-install-of-microsoft-r-server-standalone"></a>Установка изолированного сервера Microsoft R Server из командной строки

 В следующих примерах показаны аргументы, используемые при установке сервера Microsoft R Server из командной строки с помощью программы установки SQL Server.


### <a name="example-of-unattended-installation-of-r-server-standalone"></a>Пример автоматической установки изолированного сервера R Server

Выполните следующую команду из командной строки с повышенными привилегиями, чтобы установить только изолированный Microsoft R Server и его обязательные компоненты. 

```  
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR /IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS 
```  

Чтобы просмотреть ход выполнения и запросы, удалите аргумент /q.

Обратите внимание, что все следующие аргументы являются обязательными.
  - **FEATURES = SQL_SHARED_MR** возвращает только компоненты Microsoft R Server, включая Microsoft R Open и все необходимые компоненты.
  - **IACCEPTROPENLICENSETERMS** указывает, что вы приняли условия лицензионного соглашения для использования компонентов R с открытым исходным кодом.
  - **IACCEPTSQLSERVERLICENSETERMS** требуется для запуска мастера установки.


### <a name="offline-installation"></a>Автономная установка

При установке изолированного Microsoft R Server на компьютере без доступа к Интернету следует заранее скачать необходимые компоненты R и скопировать их в локальную папку. Расположения для скачивания см. в разделе [Установка компонентов R без доступа к Интернету](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md).   


## <a name="advanced-installation-tips"></a>Дополнительные советы по установке

После завершения установки можно просмотреть файл конфигурации, созданный программой установки SQL Server, а также сводку по действиям установки.

По умолчанию все журналы и сводные сведения по установке для SQL Server и связанных с ним функций записываются в `C:\Program Files\Microsoft SQL Server\140\Setup Bootstrap\Log`.

Для каждого устанавливаемого компонента создается отдельная вложенная папка. Для Microsoft R Server: 
- `RSetup.log`
- `Settings.xml`
- `Summmary<instance_GUID>.txt`

Чтобы настроить другой экземпляр Microsoft R Server с такими же параметрами, можно повторно использовать файл конфигурации, созданный во время установки. Дополнительные сведения см. в разделе [Установка SQL Server с помощью файла конфигурации](https://msdn.microsoft.com/library/dd239405.aspx).



### <a name="customizing-your-r-environment"></a>Настройка среды R

После установки можно установить дополнительные пакеты R. Дополнительные сведения см. в разделе [Установка пакетов R и управление ими](../../advanced-analytics/r-services/installing-and-managing-r-packages.md).

> [!IMPORTANT]
> Если планируется запустить код R в SQL Server, убедитесь, что на клиентском компьютере с Microsoft R Server и в экземпляре SQL Server, где выполняются службы R Services, устанавливаются одни и те же пакеты. 



## <a name="see-also"></a>См. также:  

[Microsoft R Server](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)
  