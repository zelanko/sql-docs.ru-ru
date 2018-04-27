---
title: Сохранение и выполнение пакета (мастер экспорта и импорта SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 02/16/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: import-export-data
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.saveschedule.f1
ms.assetid: b582c462-3d7a-4a4c-a2a2-2c79fedab75a
caps.latest.revision: 69
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 3ca059d4b479200a772fd326aa118f6ceecb656e
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="save-and-run-package-sql-server-import-and-export-wizard"></a>Сохранение и выполнение пакета (мастер экспорта и импорта SQL Server)
  После указания и настройки источника данных и назначения в мастере импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] откроется станица **Сохранение и запуск пакета**. На этой странице можно указать, нужно ли немедленно запустить операцию копирования. В зависимости от конфигурации также можно сохранить параметры в виде пакета [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS), чтобы настроить и использовать его позднее.
  
**Что такое пакет?** Мастер использует службы SQL Server Integration Services (SSIS) для копирования данных. В службах SSIS основной единицей является пакет. По мере перемещения по страницам и указания параметров мастер создает пакет служб SSIS в памяти.
  
## <a name="screen-shot-of-the-save-and-run-package-page"></a>Снимок экрана: страница "Сохранение и запуск пакета"  
На следующем снимке экрана показана страница мастера **Сохранение и запуск пакета** . 
   
![Страница "Сохранение и запуск пакета" в мастере импорта и экспорта](../../integration-services/import-export-data/media/save-and-run.png "Страница "Сохранение и запуск пакета" в мастере импорта и экспорта") 
  
## <a name="run-and-save-the-package"></a>Сохранение и запуск пакета 
 Чтобы продолжить, необходимо выбрать по меньшей мере один из следующих параметров.  
  
 **Run immediately**  
 Выберите этот параметр, чтобы немедленно импортировать и экспортировать данные. По умолчанию этот флажок установлен, и операция запускается немедленно.
  
 **Сохранить пакет служб SSIS**  
 Сохраните параметры в виде пакета служб SSIS. При необходимости можно позднее настроить пакет и запустить его снова. Чтобы сохранить пакет, используйте дополнительные параметры на следующей странице — **Сохранение пакета служб SSIS**.
 
Параметр сохранения пакета доступен только в том случае, если установлен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выпуска Standard Edition или более позднего.   
  
> [!NOTE]
> Если вы завершаете работу мастера и запускаете, а затем останавливаете операцию до окончания ее выполнения, пакет не сохраняется, даже если установлен флажок **Сохранить пакет служб SSIS**.  

### <a name="if-you-started-the-wizard-from-visual-studio"></a>Запуск мастера из Visual Studio
Если мастер был запущен из проекта служб Integration Services в Visual Studio с SQL Server Data Tools (SSDT):
-   Вы не можете **запустить** пакет до выхода из мастера. После выхода вы можете запустить пакет из Visual Studio.
-   Мастер **сохранит** пакет в проекте служб Integration Services, из которого был запущен мастер.

## <a name="specify-options-for-saving-the-package"></a>Указание параметров сохранения пакета
**SQL Server**  
 Выберите этот параметр, чтобы сохранить пакет в SQL Server в базе денных **msdb** в таблице **sysssispackages**.
 
> [!IMPORTANT]
> При выборе этого параметра пакет не сохраняется в базе данных каталога служб SSIS (SSISDB).  

 Выберите целевой сервер и укажите учетные данные для подключения к серверу на следующей странице — **Сохранение пакета служб SSIS**. Дополнительные сведения см. в разделе [Сохранение пакета служб SSIS](../../integration-services/import-export-data/save-ssis-package-sql-server-import-and-export-wizard.md).  
  
 **Файловая система**  
 При выборе этого параметра пакет сохраняется в файле с расширением **DTSX**.  
  
 Выберите целевую папку и имя файла для пакета на следующей странице — **Сохранение пакета служб SSIS**. Дополнительные сведения см. в разделе [Сохранение пакета служб SSIS](../../integration-services/import-export-data/save-ssis-package-sql-server-import-and-export-wizard.md).  
 
 ## <a name="specify-the-package-protection-level"></a>Указание уровня защиты пакета
 **Уровень защиты пакета**  
 Чтобы защитить данные в пакете, выберите уровень защиты в списке.  
  
 Уровень защиты определяет метод защиты (пароль или ключ пользователя) и область защиты пакетов. Защита может охватывать все данные или только конфиденциальные данные. Дополнительные сведения об уровнях защиты см. в разделе [Контроль доступа для конфиденциальных данных в пакетах](../../integration-services/security/access-control-for-sensitive-data-in-packages.md).  
  
 **Пароль**  
 Введите пароль.  
  
 **Введите пароль еще раз**  
 Введите пароль еще раз.  
  
> [!NOTE]
> Параметры для пароля доступны только в том случае, если для параметра **Уровень защиты пакета** выбрано значение, требующее указания пароля, то есть **Шифровать конфиденциальные данные паролем** или **Шифровать все данные паролем**.  

## <a name="about-the-two-pages-of-options-for-saving-the-package"></a>Сведения о двух страницах с параметрами сохранения пакета  
 Страница **Сохранение и запуск пакета** является одной из двух страниц, на которых выбираются параметры для сохранения пакета служб SSIS.  
  
-   На текущей странице выбирается тип сохранения пакета — в SQL Server или в виде файла. Здесь также указываются параметры безопасности для сохраняемого пакета.  
  
-   Далее на странице **Сохранение пакета служб SSIS** указывается имя пакета и вводятся дополнительные сведения о месте его сохранения. Дополнительные сведения см. в разделе [Сохранение пакета служб SSIS](../../integration-services/import-export-data/save-ssis-package-sql-server-import-and-export-wizard.md).  
  
 Эти параметры доступны только при выборе параметра **Сохранить пакет служб SSIS** на этой странице.  
  
## <a name="whats-next"></a>Дальнейшие действия  
 Следующая страница зависит от выбранных параметров — немедленный запуск пакета или сохранение пакета.  
  
-   Если выбран параметр для немедленного запуска, а не сохранения пакета, откроется страница **Завершение работы мастера**. На этой странице просмотрите параметры, выбранные в мастере, и запустите операцию копирования. Дополнительные сведения см. в разделе [Завершение работы мастера](../../integration-services/import-export-data/complete-the-wizard-sql-server-import-and-export-wizard.md).  
  
-   Если выбран параметр для сохранения пакета, откроется страница **Сохранение пакета служб SSIS**. На этой странице можно указать дополнительные параметры для сохранения пакета. (После сохранения пакета откроется страница **Завершение работы мастера**.) Дополнительные сведения см. в разделе [Сохранение пакета служб SSIS](../../integration-services/import-export-data/save-ssis-package-sql-server-import-and-export-wizard.md).  
  
## <a name="see-also"></a>См. также:  
[Сохранение пакетов](../../integration-services/save-packages.md)  
[Запуск пакетов служб Integration Services (SSIS)](../../integration-services/packages/run-integration-services-ssis-packages.md)  
[SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)  
[Приступая к работе с простым примером мастера импорта и экспорта](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)

  

