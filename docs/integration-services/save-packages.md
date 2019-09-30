---
title: Сохранение пакетов | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.savecopyas.f1
helpviewer_keywords:
- Integration Services packages, saving
- packages [Integration Services], saving
- saving packages
- SSIS packages, saving
- SQL Server Integration Services packages, saving
ms.assetid: 17c1de2c-637f-45c2-a148-79294bae0af4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 60dcf1692fb8b805b9eef8fad228353104131c93
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71295739"
---
# <a name="save-packages"></a>Сохранение пакетов

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] пакеты создаются с помощью конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] и сохраняются в файловой системе как XML-файлы (DTSX-файлы). Копии XML-файла пакета можно также сохранять в базе данных msdb в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или в хранилище пакетов. Хранилище пакетов представляет собой папки в определенном месте файловой системы, управляемые службами [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 При сохранении пакета в файловой системе можно в дальнейшем использовать службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , чтобы выполнить импорт пакета в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или в хранилище пакетов. Дополнительные сведения см. в разделе [Службы Integration Services (SSIS)](../integration-services/service/integration-services-service-ssis-service.md).  
  
 Можно также использовать программу командной строки **dtutil**для копирования пакета между файловой системой и базой данных msdb. Дополнительные сведения см. в статье [dtutil Utility](../integration-services/dtutil-utility.md).  
## <a name="save-a-package-to-the-file-system"></a>Сохранение пакета в файловой системе  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] с пакетом, который требуется сохранить в файле.  
  
2.  В обозревателе решений щелкните пакет, который нужно сохранить.  
  
3.  В меню **Файл** нажмите **Сохранить выбранные элементы**.  
  
    > [!NOTE]  
    >  Путь к файлу и имя, под которым был сохранен пакет, можно проверить в окне свойств.  

## <a name="save-a-copy-of-a-package"></a>Сохранение одной копии пакета
  Этот раздел описывает, как сохранить копию пакета в файле, хранилище пакетов или базе данных **msdb** в [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. При указании места сохранения копии пакета можно также обновить имя пакета.  
  
 Хранилищем пакетов может быть одновременно база данных **msdb** и папки файловой системы, только база данных **msdb**или только папки файловой системы. В базе данных **msdb**пакеты хранятся в таблице **sysdtspackages90** . Эта таблица содержит столбец **folderid** , который идентифицирует логический каталог, которому принадлежит пакет. Логические каталоги предоставляют полезный способ группировки пакетов, сохраненных в базе данных **msdb** так же как файловая система предоставляет способ группировки пакетов, сохраненных в файловой системе. Строки в таблице **sysdtspackagefolders90** в базе данных **msdb** определяют папки.  
  
 Если база данных **msdb** не определена как часть хранилища пакетов, то при выборе SQL Server в параметре **Путь к пакету** можно продолжить связывание пакетов с существующими логическими папками.  
  
> [!NOTE]  
>  Чтобы сохранить копию пакета, необходимо открыть пакет в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
### <a name="to-save-a-copy-of-a-package"></a>Сохранение копии пакета  
  
1.  В обозревателе решений дважды щелкните пакет, копию которого необходимо сохранить.  
  
2.  В меню **Файл** выберите пункт **Сохранить копию \<файл пакета> как**.  
  
3.  В диалоговом окне **Сохранение копии пакета** выберите размещение пакета в списке **Размещение пакета** . Доступны следующие параметры:  
    -   SQL Server
    -   Файловая система 
    -   Хранилище пакетов служб SSIS 
  
4.  Если для размещения пакета выбран **SQL Server** или **Хранилище пакетов служб SSIS**, то введите имя сервера.  
  
5.  Если сохранение производится в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], укажите тип проверки подлинности а если используется проверка подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , введите имя пользователя и пароль.  
  
6.  Чтобы указать путь к пакету, введите путь к пакету или нажмите кнопку обзора **(…)** и укажите расположение пакета. Стандартное имя пакета — Пакет. При необходимости замените имя пакета на нужное.  
  
     При выборе **SQL Server** в качестве значения параметра **Путь к пакету** путь к пакету состоит из логических папок в базе данных **msdb** и имени пакета. Например, если пакет DownloadMonthlyData связан с каталогом Finance в каталоге MSDB (имя по умолчанию корневого логического каталога в базе данных **msdb**), то путь к пакету DownloadMonthlyData выглядит как MSDB/Finance/DownloadMonthlyData  
  
     Если в качестве значения параметра **Путь к пакету** выбирается **Хранилище пакетов служб SSIS** , путь к пакету состоит из каталога, которым управляют службы Integration Services. Например, если пакет UpdateDeductions находится в папке HumanResources — в папке файловой системы, которой управляет служба, то путь к пакету выглядит как /File System/HumanResources/UpdateDeductions; аналогично: если пакет PostResumes связан с папкой HumanResources в папке MSDB, то путь к пакету выглядит как MSDB/HumanResources/PostResumes.  
  
     При выборе **Файловой системы** в качестве значения параметра **Путь к пакету** , путь к пакету представляет собой имя в файловой системе и имя файла. Например, если имя пакета UpdateDemographics, то путь к пакету выглядит как C:\HumanResources\Quarterly\UpdateDemographics.dtsx.  
  
7.  Просмотрите уровень защиты пакета.  
  
8.  Для изменения уровня защиты нажмите кнопку обзора **(…)** возле поля **Уровень защиты**.  
  
    -   В диалоговом окне **Уровень защиты пакета** выберите иной уровень защиты.  
  
    -   Нажмите кнопку **ОК**.  
  
9. Нажмите кнопку **ОК**.  

## <a name="save-a-package-as-a-package-template"></a>Сохранение пакета в качестве шаблона пакета
 В этом разделе описано, как обозначить и использовать пользовательские пакеты в виде шаблонов при создании новых пакетов служб Integration Services в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. По умолчанию в службах [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] используется шаблон пакета, который создает пустой пакет при добавлении нового пакета в проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Этот шаблон по умолчанию заменить нельзя, однако можно добавить новые шаблоны.  
  
 Для использования в роли шаблонов можно назначить несколько пакетов. Прежде чем сделать из пользовательского пакета шаблон, необходимо создать сам пакет.  
  
 При создании пакета с помощью пользовательских пакетов в виде шаблонов новые пакеты имеют те же имя и код GUID, что и шаблон. Чтобы различать пакеты, необходимо обновить значение свойства **Name** и создать новый код GUID для свойства **ID** . Дополнительные сведения см. в разделах [Создание пакетов в SQL Server Data Tools](../integration-services/create-packages-in-sql-server-data-tools.md) и [Установка свойства пакета](../integration-services/set-package-properties.md).  
  
### <a name="to-designate-a-custom-package-as-a-package-template"></a>Обозначение пользовательского пакета как шаблона пакета  
  
1.  Найдите в файловой системе пакет, который нужно использовать в роли шаблона.  
  
2.  Скопируйте пакет в папку DataTransformationItems. По умолчанию эта папка находится в каталоге «C:\Program Files\Microsoft Visual Studio 9,0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject».  
  
3.  Повторите шаги 1 и 2 для каждого пакета, который нужно использовать в качестве шаблона.  
  
### <a name="to-use-a-custom-package-as-a-package-template"></a>Чтобы использовать пользовательский пакет как шаблон пакета  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , в котором необходимо создать пакет.  
  
2.  В обозревателе решений щелкните проект правой кнопкой мыши, укажите **Добавить** и выберите **Новый элемент**.  
  
3.  В диалоговом окне **Добавление нового элемента — \<имя проекта>** щелкните пакет, который нужно использовать в качестве шаблона.  
  
     Список шаблонов включает шаблон пакетов по умолчанию с именем «Новый пакет служб SSIS». Значок пакета определяет шаблоны, которые можно использовать в качестве шаблонов пакетов.  
  
4.  Нажмите кнопку **Добавить**.  
