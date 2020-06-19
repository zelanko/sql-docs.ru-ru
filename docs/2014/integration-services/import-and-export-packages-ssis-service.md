---
title: Импорт и экспорт пакетов (службы SSIS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], importing
- packages [Integration Services], exporting
- importing packages
- exporting packages
ms.assetid: ef18ec11-b536-47d9-abd1-794099f43486
author: janinezhang
ms.author: janinez
ms.openlocfilehash: ce04befcb4c8558216cecded6cb1892c3106295f
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84965684"
---
# <a name="import-and-export-packages-ssis-service"></a>Импорт и экспорт пакетов (службы SSIS)
    
> [!IMPORTANT]  
>  В данном разделе описывается компонент [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] — служба Windows для управления пакетами служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] поддерживает эту службу для обеспечения обратной совместимости с более ранними версиями служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Начиная с [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], на сервере служб Integration Services можно управлять пакетами.  
  
 Пакеты можно сохранять либо в таблице sysssispackages базы данных msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , либо в файловой системе.  
  
 Хранилище пакетов, являющееся логическим хранилищем, которое контролируется службой [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , может включать и базу данных msdb, и папки файловой системы, указанные в файле конфигурации для службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 Можно выполнять импорт и экспорт пакетов между следующими типами хранилищ:  
  
-   Папки файловой системы в любом месте этой файловой системы.  
  
-   Папки в хранилище пакетов служб SSIS. Две папки по умолчанию с именами File System и MSDB.  
  
-   База данных msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] предоставляют возможность для импорта и экспорта пакетов и посредством этого изменения формата и места хранения пакетов. С помощью функций импорта и экспорта можно добавлять пакеты в файловую систему, хранилище пакетов или базу данных msdb, а также копировать пакеты из одного формата хранения в другой. Например, пакеты, сохраненные в msdb, можно скопировать в файловую систему и наоборот.  
  
 Можно также скопировать пакет в другой формат с помощью программы командной строки **dtutil** (dtutil.exe). Дополнительные сведения см. в статье [dtutil Utility](dtutil-utility.md).  
  
## <a name="to-import-or-export-a-package"></a>Импорт и экспорт пакетов  
  
> [!IMPORTANT]  
>  В этом разделе обсуждается служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , входящая в состав [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]. [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] поддерживает службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] для обеспечения обратной совместимости с [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]. Сведения об управлении пакетами в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] см. в разделе [Сервер служб Integration Services (SSIS)](catalog/integration-services-ssis-server-and-catalog.md).  
  
 Можно выполнять импорт и экспорт пакетов служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] между следующими типами хранилищ.  
  
-   Можно импортировать пакет, хранящийся в экземпляре [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , в файловой системе или в [!INCLUDE[ssIS](../includes/ssis-md.md)] хранилище пакетов. Импортированные пакеты сохраняются в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или в папке хранилища пакетов служб [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
-   Можно экспортировать пакеты, хранящиеся в экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], в файловой системе или хранилище пакетов служб [!INCLUDE[ssIS](../includes/ssis-md.md)] , в другой формат хранения и в другое расположение.  
  
 Однако существует ряд ограничений на импорт и экспорт пакетов между разными версиями [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:  
  
-   С экземпляра [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]можно импортировать пакеты из экземпляра [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], но нельзя экспортировать их в экземпляр [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)].  
  
-   С экземпляра [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]нельзя импортировать пакеты из экземпляра [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]или экспортировать их туда.  
  
 В следующих разделах описывается импорт и экспорт пакетов с помощью среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] .  
  
#### <a name="to-import-a-package-by-using-sql-server-management-studio"></a>Импорт пакета с помощью среды SQL Server Management Studio  
  
1.  Нажмите кнопку **Пуск**, укажите пункт **Microsoft** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и выберите пункт **SQL Server Management Studio**.  
  
2.  В диалоговом окне **Соединение с сервером** установите следующие параметры.  
  
    -   В поле **Тип сервера** выберите **Службы Integration Services**.  
  
    -   В поле **имя сервера** введите имя сервера или нажмите **\<Browse for more...>** и выберите сервер для использования.  
  
3.  Если обозреватель объектов не открыт, в меню **Вид** выберите пункт **Обозреватель объектов**.  
  
4.  В обозревателе объектов разверните папку « **Сохраненные пакеты** ».  
  
5.  Разверните вложенные папки и найдите папку, в которую нужно выполнить импорт пакета.  
  
6.  Щелкните папку правой кнопкой мыши и выберите пункт **Импорт пакета**. А затем выполните одно из следующих действий:  
  
    -   Чтобы выполнить импорт из экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], выберите параметр **SQL Server** и укажите сервер и метод проверки подлинности. При выборе проверки подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] укажите имя пользователя и пароль.  
  
         Нажмите кнопку обзора **(…)**, выберите импортируемый пакет и нажмите кнопку **ОК**.  
  
    -   Чтобы выполнить импорт из файловой системы, выберите параметр **Файловая система** .  
  
         Нажмите кнопку обзора **(…)**, выберите импортируемый пакет и нажмите кнопку **Открыть**.  
  
    -   Чтобы выполнить импорт из хранилища пакетов служб [!INCLUDE[ssIS](../includes/ssis-md.md)] , укажите сервер в поле **Хранилище пакетов служб SSIS** .  
  
         Нажмите кнопку обзора **(…)**, выберите импортируемый пакет и нажмите кнопку **ОК**.  
  
7.  При необходимости обновите название пакета.  
  
8.  Чтобы обновить уровень защиты пакета, нажмите кнопку обзора **(…)** и выберите иной уровень защиты с помощью диалогового окна **Уровень защиты пакета**. При выборе параметра **Шифровать конфиденциальные данные паролем** или **Шифровать все данные паролем** введите и подтвердите пароль.  
  
9. Чтобы завершить импорт, нажмите кнопку **ОК** .  
  
#### <a name="to-export-a-package-by-using-sql-server-management-studio"></a>Экспорт пакета с помощью среды SQL Server Management Studio  
  
1.  Нажмите кнопку **Пуск**, укажите пункт **Microsoft** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и выберите пункт **SQL Server Management Studio**.  
  
2.  В диалоговом окне **соединение с сервером** задайте следующие параметры.  
  
    -   В поле **Тип сервера** выберите **Службы Integration Services**.  
  
    -   В поле **имя сервера** введите имя сервера или нажмите **\<Browse for more...>** и выберите сервер для использования.  
  
3.  Если обозреватель объектов не открыт, в меню **Вид** выберите пункт **Обозреватель объектов**.  
  
4.  В обозревателе объектов разверните папку **Сохраненные пакеты** .  
  
5.  Разверните вложенные папки и выберите пакет для экспорта.  
  
6.  Щелкните правой кнопкой мыши пакет, выберите пункт **Экспорт**и выполните одно из следующих действий:  
  
    -   Чтобы выполнить экспорт в экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], выберите **SQL Server** , затем определите сервер и выберите режим проверки подлинности. При выборе проверки подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] укажите имя пользователя и пароль.  
  
         Нажмите кнопку обзора **(…)** и разверните папку **Пакеты служб SSIS**, чтобы выбрать папку, в которую нужно сохранить пакет. При необходимости измените имя пакета по умолчанию и нажмите кнопку **ОК**.  
  
    -   Чтобы выполнить экспорт в файловую систему, выберите параметр **Файловая система** .  
  
         Нажмите кнопку обзора **(…)**, чтобы выбрать папку, в которую нужно экспортировать пакет, введите имя файла пакета и нажмите кнопку **Сохранить**.  
  
    -   Чтобы выполнить экспорт в хранилище пакетов служб [!INCLUDE[ssIS](../includes/ssis-md.md)] , выберите **Хранилище пакетов служб SSIS** и укажите сервер.  
  
         Нажмите кнопку обзора **(…)**, разверните папку **Пакеты служб SSIS** и выберите папку, в которую нужно сохранить пакет. Если нужно изменить имя пакета, введите новое имя в текстовое поле **Имя пакета** . [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Чтобы обновить уровень защиты пакета, нажмите кнопку обзора **(…)** и выберите иной уровень защиты с помощью диалогового окна **Уровень защиты пакета**. При выборе параметра **Шифровать конфиденциальные данные паролем** или **Шифровать все данные паролем** введите и подтвердите пароль.  
  
8.  Чтобы завершить экспорт, нажмите кнопку **ОК** .  
  
## <a name="see-also"></a>См. также:  
 [Управление пакетами (службы SSIS)](service/package-management-ssis-service.md)  
  
  
