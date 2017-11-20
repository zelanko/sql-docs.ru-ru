---
title: "Сохранить пакет служб SSIS (мастер экспорта и импорта SQL Server) | Документы Microsoft"
ms.custom: 
ms.date: 02/17/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.savedtspackage.f1
ms.assetid: 7bf8ac6a-5599-43ab-bf5c-e072c11b85a0
caps.latest.revision: 64
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: 6ebbab742350e6874b86213c1fbf516e095a1e9a
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="save-ssis-package-sql-server-import-and-export-wizard"></a>Сохранение пакета служб SSIS (мастер экспорта и импорта SQL Server)
  Если вы указали на **сохранить и запустить пакет** страницы, который вы хотите сохранить их в виде пакета SQL Server Integration Services (SSIS), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] показан мастер импорта и экспорта **Сохранение пакета служб SSIS**. На этой странице можно указать дополнительные параметры для сохранения пакета, созданного с помощью мастера.  

Параметры, которые вы видите на странице **Сохранение пакета служб SSIS** , зависят от выбора, сделанного ранее на странице **Сохранение и запуск пакета** и касающегося сохранения пакета в SQL Server или в файловой системе. Чтобы ознакомиться с описанием страницы **Сохранение и запуск пакета** , см. раздел [Сохранение и запуск пакета](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md).
 
**Что такое пакет?** Мастер использует службы SQL Server Integration Services (SSIS) для копирования данных. В службах SSIS основной единицей является пакет. По мере перемещения по страницам и указания параметров мастер создает пакет служб SSIS в памяти.

## <a name="screen-shot---common-options"></a>Снимок - экрана общих параметров
На следующем снимке экрана показаны в первой части **Сохранение пакета служб SSIS** странице мастера. Остальная часть страницы имеет переменное число параметров, которые зависят от выбранного назначения пакетов.

![Сохранение пакета - Общие параметры](../../integration-services/import-export-data/media/save-package-common-options.png)

## <a name="provide-a-name-and-description-for-the-package"></a>Укажите имя и описание пакета  
 **Название**  
 Введите уникальное имя пакета.  
  
 **Описание**  
 Введите описание пакета. Рекомендуется описать назначение пакета, чтобы сделать работу с пакетами проще и понятнее.  
  
 **Цель**  
 Назначение ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или файловая система), указанное ранее для пакета. Если вы хотите сохранить пакет в другом назначении, вернитесь на страницу **Сохранение и запуск пакета** .

## <a name="screen-shot---save-the-package-in-sql-server"></a>Снимок экрана: сохранение пакета в SQL Server

 На следующем снимке экрана показано **Сохранение пакета служб SSIS** мастера, если вы выбрали **SQL Server** параметр **сохранить и запустить пакет** страницы. 
  
![Сохранить пакет служб SSIS страница мастера импорта и экспорта](../../integration-services/import-export-data/media/save-package2.png "Сохранение пакета служб SSIS страница мастера импорта и экспорта")  

## <a name="options-to-specify-target--sql-server"></a>Параметры, задающие (Target = SQL Server) 

 > [!NOTE]
 > Мастер сохраняет пакет в **msdb** базы данных в **sysssispackages** таблицы. Этого параметра **не** сохранить пакет в базу данных каталога служб SSIS (SSISDB).  
 
 **Имя сервера**  
 Введите или выберите имя целевого сервера.  
   
 **Использовать проверку подлинности Windows**  
Подключитесь к серверу, используя встроенную проверку подлинности Windows. Предпочтителен этот метод проверки подлинности.  
  
 **Использовать проверку подлинности SQL Server**  
Подключитесь к серверу, используя проверку подлинности SQL Server.  
  
 **Имя пользователя**  
Если указана проверка подлинности SQL Server, введите имя пользователя.  
  
 **Пароль**  
Если указана проверка подлинности SQL Server, введите пароль.  
    
## <a name="screen-shot---save-the-package-in-the-file-system"></a>Снимок экрана: сохранение пакета в файловой системе
 
На следующем снимке экрана показано **Сохранение пакета служб SSIS** мастера, если вы выбрали **файловая система** параметр **сохранить и запустить пакет** страницы. 
  
![Сохранить пакет служб SSIS страница мастера импорта и экспорта](../../integration-services/import-export-data/media/save-package1.png "Сохранение пакета служб SSIS страница мастера импорта и экспорта")  

## <a name="options-to-specify-target--file-system"></a>Параметры, задающие (Target = файловая система)

 **Имя файла**  
 Введите путь и имя файла для целевого файла или используйте **Обзор** кнопку, чтобы выбрать место назначения.  
  
> [!TIP]
> Обязательно укажите папку назначения, введя его или просмотра. Если введено только имя файла без пути, вы не знаете, где мастер сохраняет пакет. Кроме того, мастер может попытаться сохранить пакет в расположении, где у него нет разрешения на сохранение файлов, что приводит к ошибке.  
>   
>  Запомните, где именно сохранен пакет.  
  
 **Обзор**  
 При необходимости просмотреть и выбрать путь к файлу назначения в **Сохранение пакета** диалоговое окно.  

## <a name="about-the-two-pages-of-options-for-saving-the-package"></a>Сведения о двух страницах с параметрами сохранения пакета  
 Страница **Сохранение пакета служб SSIS** является одной из двух страниц, на которых выбираются параметры для сохранения пакета служб SSIS.  
  
-   На предыдущей странице **Сохранение и выполнение пакета**выбирается тип сохранения пакета — в SQL Server или в виде файла. Здесь также указываются параметры безопасности для сохраняемого пакета. Чтобы ознакомиться с описанием страницы **Сохранение и запуск пакета** , см. раздел [Сохранение и запуск пакета](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md).  
  
-   На текущей странице указывается имя пакета и вводятся дополнительные сведения о месте его сохранения.  
 
## <a name="run-the-saved-package-again-later"></a>Повторный запуск сохраненного пакета  
 Сведения о том, как снова запустить сохраненный пакет, см. в одном из следующих разделов:  
  
-   Чтобы запустить пакет с помощью служебной программы с удобным пользовательским интерфейсом, см. раздел [Справочник по пользовательскому интерфейсу программы выполнения пакетов (DtExecUI)](../../integration-services/packages/execute-package-utility-dtexecui-ui-reference.md).  
  
-   Чтобы запустить пакет из командной строки или из пакетного файла, см. раздел [Программа dtexec](../../integration-services/packages/dtexec-utility.md).  
  
-   Если пакет сохранен в базе данных **msdb** SQL Server, подключитесь к службам Integration Services. Затем обозревателе объектов в среде SQL Server Management Studio перейдите к окну **Сохраненные пакеты | MSDB**, щелкните пакет правой кнопкой мыши и выберите **Выполнить пакет**.

-   Если пакет сохранен в файловой системе, см. раздел [Запуск пакетов служб Integration Services (SSIS)](../../integration-services/packages/run-integration-services-ssis-packages.md) для запуска пакета в среде разработки. прежде чем открыть и запустить пакет, следует добавить его в проект служб Integration Services.  

## <a name="customize-the-saved-package"></a>Настройка сохраненного пакета  
 Дополнительные сведения о настройке сохраненного пакета см. в разделе [Пакеты служб Integration Services (SSIS)](../../integration-services/integration-services-ssis-packages.md).  
  
## <a name="whats-next"></a>Дальнейшие действия  
 После указания дополнительных параметров для сохранения пакета выполняется переход на страницу **Завершение работы мастера**. На этой странице просмотрите параметры, выбранные в мастере, и запустите операцию. Дополнительные сведения см. в разделе [Завершение работы мастера](../../integration-services/import-export-data/complete-the-wizard-sql-server-import-and-export-wizard.md).  
 
## <a name="see-also"></a>См. также:  
[Сохранение пакетов](../../integration-services/save-packages.md)  
[Запуск пакетов служб Integration Services (SSIS)](../../integration-services/packages/run-integration-services-ssis-packages.md)  
[SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)
 
 

