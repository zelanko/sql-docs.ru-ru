---
title: Сохранение копии пакета | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, saving
- packages [Integration Services], saving
- saving packages
- SSIS packages, saving
- SQL Server Integration Services packages, saving
ms.assetid: 21482a20-e420-4452-b7eb-8f9fa1929f31
author: janinezhang
ms.author: janinez
ms.openlocfilehash: d4725d05e41ae6335ceae19c46c2c36af14dbcf8
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84964404"
---
# <a name="save-a-copy-of-a-package"></a>Сохранение одной копии пакета
  Эта процедура описывает, как сохранить копию пакета в файле, хранилище пакетов или базе данных **msdb** в [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. При указании места сохранения копии пакета можно также обновить имя пакета.  
  
 Хранилищем пакетов может быть одновременно база данных **msdb** и папки файловой системы, только база данных **msdb**или только папки файловой системы. В базе данных **msdb**пакеты хранятся в таблице **sysdtspackages90** . Эта таблица содержит столбец **folderid** , который идентифицирует логический каталог, которому принадлежит пакет. Логические каталоги предоставляют полезный способ группировки пакетов, сохраненных в базе данных **msdb** так же как файловая система предоставляет способ группировки пакетов, сохраненных в файловой системе. Строки в таблице **sysdtspackagefolders90** в базе данных **msdb** определяют папки.  
  
 Если база данных **msdb** не определена как часть хранилища пакетов, то при выборе SQL Server в параметре **Путь к пакету** можно продолжить связывание пакетов с существующими логическими папками.  
  
> [!NOTE]  
>  Чтобы сохранить копию пакета, необходимо открыть пакет в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
### <a name="to-save-a-copy-of-a-package"></a>Сохранение копии пакета  
  
1.  В обозревателе решений дважды щелкните пакет, копию которого необходимо сохранить.  
  
2.  В меню **файл** выберите команду **сохранить копию \<package file> как**.  
  
3.  В диалоговом окне **Сохранение копии пакета** выберите размещение пакета в списке **Размещение пакета** .  
  
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
  
## <a name="see-also"></a>См. также:  
 [Integration Services &#40;пакетов&#41; SSIS](../../2014/integration-services/integration-services-ssis-packages.md)   
 [Настройка служб Integration Services (службы SSIS)](service/integration-services-service-ssis-service.md)  
  
  
