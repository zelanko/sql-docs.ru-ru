---
title: "Установка и изменение уровня защиты пакетов | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "пароли [службы Integration Services]"
  - "пакеты [службы Integration Services], безопасность"
  - "безопасность [службы Integration Services], уровни защиты"
  - "уровень защиты для пакетов [службы Integration Services]"
ms.assetid: 904a5580-82ba-4a26-b0c5-d1c989975f61
caps.latest.revision: 10
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# Установка и изменение уровня защиты пакетов
  Для управления доступом к содержимому пакетов и конфиденциальным данным в них, таким как пароли, необходимо задать значение свойства **ProtectionLevel** . Пакеты, которые содержатся в проекте, должны обладать тем же уровнем защиты, что и сам проект. Это необходимо для создания проекта. При изменении настройки свойства **ProtectionLevel** в проекте потребуется вручную обновить настройку свойства для пакетов.  
  
 Дополнительные сведения о том, как определить параметры **ProtectionLevel** , подходящие для пакетов на различных этапах их жизненных циклов, см. в разделе [Access Control for Sensitive Data in Packages](../../integration-services/packages/access-control-for-sensitive-data-in-packages.md). Общие сведения о средствах безопасности в службах [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] см. в разделе [Общие сведения о безопасности (службы Integration Services)](../../integration-services/security/security-overview-integration-services.md).  
  
 В приведенной в данном разделе процедуре описано использование [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] или средства командной dtutil для изменения свойства **ProtectionLevel** .  
  
> [!NOTE]  
>  В дополнение к приведенной в этом разделе процедуре можно, как правило, задать или изменить свойство пакета **ProtectionLevel** при импорте или экспорте пакета. Если сохранение пакета производится с помощью мастера импорта и экспорта **ProtectionLevel** , то можно также изменить свойство [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### Установка или изменение уровня защиты пакета в SQL Server Data Tools  
  
1.  Просмотрите доступные значения свойства **ProtectionLevel** в разделе [Установка уровня защиты пакетов](../../integration-services/packages/access-control-for-sensitive-data-in-packages.md)и выберите подходящее значение для своего пакета.  
  
2.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий пакет.  
  
3.  Откройте пакет в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
4.  Если свойства пакета не отображаются в окне свойств, щелкните область конструктора.  
  
5.  В окне свойств в группе **Безопасность** выберите подходящее значение для свойства **ProtectionLevel** .  
  
     Если выбран уровень защиты, для которого требуется пароль, введите пароль в качестве значения свойства **PackagePassword** .  
  
6.  Чтобы сохранить пакет, в меню **Файл** выберите пункт **Сохранить выбранные элементы** .  
  
### Установка или изменение уровня защиты пакетов в командной строке  
  
1.  Просмотрите доступные значения свойства **ProtectionLevel** в разделе [Установка уровня защиты пакетов](../../integration-services/packages/access-control-for-sensitive-data-in-packages.md)и выберите подходящее значение для своего пакета.  
  
2.  Просмотрите сопоставления для параметра **Encrypt** в разделе [dtutil Utility](../../integration-services/dtutil-utility.md)и выберите подходящее целое число, которое будет значением выбранного свойства **ProtectionLevel** .  
  
3.  Откройте окно командной строки.  
  
4.  В командной строке перейдите к папке с пакетом или пакетами, для которых требуется задать свойство **ProtectionLevel** .  
  
     В примерах синтаксиса в следующем шаге предполагается, что эта папка является текущей папкой.  
  
5.  Установите или измените уровень защиты пакета или пакетов при помощи команды, подобно показанной в одном из следующих примеров.  
  
    -   Следующая команда задает свойство **ProtectionLevel** отдельного пакета в файловой системе равным уровню 2 – «Шифровать конфиденциальные данные паролем» с паролем «strongpassword»:  
  
         `dtutil.exe /file "C:\Package.dtsx" /encrypt file;"C:\Package.dtsx";2;strongpassword`  
  
    -   Следующая команда задает свойство **ProtectionLevel** всех пакетов в определенной папке файловой системы равным уровню 2 – «Шифровать конфиденциальные данные паролем» с паролем «strongpassword»:  
  
         `for %f in (*.dtsx) do dtutil.exe /file %f /encrypt file;%f;2;strongpassword`  
  
         Если подобную команду использовать в пакетном файле, то в него необходимо включить заполнитель «%f» в виде «%%f».  
  
## См. также  
 [Программа dtutil](../../integration-services/dtutil-utility.md)  
  
  