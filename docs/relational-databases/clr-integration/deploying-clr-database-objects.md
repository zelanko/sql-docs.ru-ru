---
title: "Развертывание объектов базы данных CLR | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- deployment script [CLR integration]
- common language runtime [SQL Server], deploying
- deploying assemblies [CLR integration]
- deploying [CLR integration]
ms.assetid: 00752573-3367-41a7-af98-7b7a29e8e2f2
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: c5fd0a8abac60e2e5b0e2f1bce35bd1d6e3554e1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="deploying-clr-database-objects"></a>Развертывание объектов базы данных CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Развертывание — это процесс, распространять готовое приложение или модуль, чтобы установить и запустить на другом компьютере. С помощью среды [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio можно разрабатывать объекты базы данных среды CLR и развертывать их на тестовом сервере. Вместо среды Visual Studio управляемые объекты базы данных можно компилировать с помощью файлов распространения платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework. После компиляции сборки, содержащие объекты базы данных CLR можно развернуть на тестовом сервере с помощью среды Visual Studio или инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)]. Обратите внимание, что среду Visual Studio .NET 2003 нельзя использовать для программирования или развертывания в интеграции со средой CLR. В состав [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входит предварительно установленная платформа .NET Framework, а Visual Studio .NET 2003 не может использовать сборки .NET Framework версии 2.0.  
  
 После тестирования и проверки методов CLR на тестовом сервере их можно распространить на рабочих серверах с помощью скрипта развертывания. Скрипт развертывания можно создать вручную или с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (см. процедуру далее в этом разделе).  
  
 Функция интеграции со средой CLR отключена в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию, поэтому ее нужно включить, чтобы использовать сборки CLR. Дополнительные сведения см. в статье [Enabling CLR Integration](../../relational-databases/clr-integration/clr-integration-enabling.md).  
  
## <a name="deploying-the-assembly-to-the-test-server"></a>Развертывание сборки на тестовом сервере  
 С помощью среды Visual Studio можно разрабатывать функции CLR, процедуры, триггеры, определяемые пользователем типы или определяемые пользователем статистические функции и развертывать их на тестовом сервере. Эти управляемые объекты базы данных также можно скомпилировать с помощью компиляторов командной строки, таких как csc.exe и vbc.exe, входящих в состав файлов распространения платформы .NET Framework. Для разработки управляемых объектов базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] наличие интегрированной среды разработки Visual Studio не требуется.  
  
 Убедитесь, что все ошибки и предупреждения компилятора устранены. Сборки, содержащие процедуры CLR, можно зарегистрировать в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью среды Visual Studio или инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!NOTE]  
>  Чтобы использовать среду [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Visual Studio для удаленной разработки, отладки и разработки, в экземпляре [!INCLUDE[msCoName](../../includes/msconame-md.md)] должен быть включен протокол TCP/IP. Дополнительные сведения о включении протокола TCP/IP на сервере см. в разделе [Настройка клиентских протоколов](../../database-engine/configure-windows/configure-client-protocols.md).  
  
#### <a name="to-deploy-the-assembly-using-visual-studio"></a>Развертывание сборки с помощью среды Visual Studio  
  
1.  Постройте проект, выбрав **построения** \<имя проекта > из **построения** меню.  
  
2.  Перед развертыванием сборки на тестовом сервере устраните все ошибки и предупреждения, полученные во время построения.  
  
3.  Выберите **развернуть** из **построения** меню. Сборка будет зарегистрирована в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и базе данных, указанной при создании проекта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в среде Visual Studio.  
  
#### <a name="to-deploy-the-assembly-using-transact-sql"></a>Развертывание сборки с помощьюTransact-SQL  
  
1.  Выполните компиляцию сборки из исходного файла с помощью компиляторов командной строки из состава платформы .NET Framework.  
  
2.  Для файлов с исходным кодом на языке [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#:  
  
3.  `csc /target:library C:\helloworld.cs`  
  
4.  Для файлов с исходным кодом на языке [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic:  
  
 `vbc /target:library C:\helloworld.vb`  
  
 Эти команды запускают Visual C# или Visual Basic с помощью компилятора **/target-** параметр, чтобы указать построение библиотеки DLL.  
  
1.  Перед развертыванием сборки на тестовом сервере устраните все ошибки и предупреждения, полученные во время построения.  
  
2.  Откройте на тестовом сервере среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Создайте новый запрос, соединенный с подходящей тестовой базой данных (например AdventureWorks).  
  
3.  Создайте сборку на сервере, добавив в запрос следующую инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 `CREATE ASSEMBLY HelloWorld from 'c:\helloworld.dll' WITH PERMISSION_SET = SAFE;`  
  
1.  Процедура, функция, статистическое выражение, определяемый пользователем тип или триггер должны быть созданы в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если **HelloWorld** сборка содержит метод с именем **HelloWorld** в **процедуры** следующие [!INCLUDE[tsql](../../includes/tsql-md.md)] можно добавить в запрос для создания Вызванная процедура **hello** в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 `CREATE PROCEDURE hello`  
  
 `AS`  
  
 `EXTERNAL NAME HelloWorld.Procedures.HelloWorld`  
  
 Дополнительные сведения о создании различных типов управляемых объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в разделе [определяемые пользователем функции](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md), [пользовательские агрегатные функции](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md), [со средой CLR Определяемые пользователем типы](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md), [хранимые процедуры CLR](http://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33), и [триггеры CLR](http://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c).  
  
## <a name="deploying-the-assembly-to-production-servers"></a>Развертывание сборки на рабочих серверах  
 После тестирования и проверки CLR-объектов базы данных на тестовом сервере их можно распространить на рабочих серверах с помощью сценария развертывания. Дополнительные сведения об отладке управляемых объектов базы данных см. в разделе [отладки объектов базы данных CLR](../../relational-databases/clr-integration/debugging-clr-database-objects.md).  
  
 Развертывание управляемых объектов базы данных аналогично развертыванию обычных объектов базы данных (таблиц, процедур [!INCLUDE[tsql](../../includes/tsql-md.md)] и т. д.). Сборки, содержащие CLR-объекты базы данных, можно развертывать на других серверах с помощью скрипта развертывания. Скрипт развертывания создается с помощью функции «Создание скриптов» среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Скрипт развертывания можно создать вручную или с помощью функции «Создание скриптов», после чего изменить вручную. После создания скрипта развертывания его можно запустить на других экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для развертывания управляемых объектов базы данных.  
  
#### <a name="to-generate-a-deployment-script-using-generate-scripts"></a>Создание скрипта развертывания с помощью функции создания скриптов  
  
1.  Откройте среду [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] и соединитесь с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в котором зарегистрирована управляемая сборка или объект баз данных, который необходимо развернуть.  
  
2.  В **обозревателя объектов**, разверните  **\<имя сервера >** и **баз данных** деревьев. Щелкните правой кнопкой мыши базу данных, где управляемого объекта базы данных не зарегистрирован, выберите **задачи**, а затем выберите **сформировать сценарии**. Откроется мастер скриптов.  
  
3.  Выберите базу данных из списка и нажмите кнопку **Далее**.  
  
4.  В **Выбор параметров скрипта** области, нажмите кнопку **Далее**, или измените параметры и нажмите кнопку **Далее**.  
  
5.  В **Выбор типов объектов** области, выберите тип объекта базы данных для развертывания. Нажмите кнопку **Далее**.  
  
6.  Для каждого типа объекта, выбранного в **Выбор типов объектов** области **Выбор \<типа >** представлены области. На этой панели можно выбирать из всех экземпляров этого типа объекта базы данных, зарегистрированного в указанной базе данных. Выберите один или несколько объектов и щелкните **Далее**.  
  
7.  **Параметры вывода** появится панель все нужные базы данных объектов, выбранных типов. Выберите **вывести скрипт в файл** и укажите путь к файлу сценария. Выберите **Далее**. Просмотрите выбранные параметры и нажмите кнопку **Готово**. Скрипт развертывания сохранится в указанном файле.  
  
## <a name="post-deployment-scripts"></a>Скрипты, выполняемые после развертывания  
 Существует возможность запуска скриптов, выполняемых после развертывания.  
  
 Чтобы добавить такой скрипт, необходимо добавить файл с именем postdeployscript.sql в каталог проекта Visual Studio. Например, щелкните правой кнопкой мыши проект в **обозревателе решений** и выберите **Добавление существующего элемента**. Добавьте файл в корневой каталог проекта, а не в папку «Тестовые скрипты».  
  
 При выполнении развертывания среда Visual Studio запустит данный скрипт после развертывания проекта.  
  
## <a name="see-also"></a>См. также:  
 [Основные понятия о программировании интеграции со средой (CLR)](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  
