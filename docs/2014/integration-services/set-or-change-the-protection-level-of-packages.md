---
title: Установка или изменение уровня защиты пакетов | Документы Microsoft
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- passwords [Integration Services]
- packages [Integration Services],security
- security [Integration Services],protection levels
- protection level for packages [Integration Services]
ms.assetid: 904a5580-82ba-4a26-b0c5-d1c989975f61
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 695667f3ba50b6cde3d2b9629e7116fecf7c4b16
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191651"
---
# <a name="set-or-change-the-protection-level-of-packages"></a>Установка и изменение уровня защиты пакетов
  Для управления доступом к содержимому пакетов и конфиденциальным данным в них, таким как пароли, необходимо задать значение свойства `ProtectionLevel`. Пакеты, которые содержатся в проекте, должны обладать тем же уровнем защиты, что и сам проект. Это необходимо для создания проекта. При изменении настройки свойства `ProtectionLevel` в проекте потребуется вручную обновить настройку свойства для пакетов.  
  
 Сведения о том, как определить `ProtectionLevel` параметры, подходящие для пакетов на различных этапах жизненного цикла пакета, в разделе [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md). Общие сведения о средствах безопасности в службах [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] см. в разделе [Общие сведения о безопасности (службы Integration Services)](security/security-overview-integration-services.md).  
  
 В этом разделе описывается, как использовать [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] или средства командной dtutil для изменения `ProtectionLevel` свойство.  
  
> [!NOTE]  
>  Помимо процедуры, описанные в этом разделе, обычно можно задать или изменить `ProtectionLevel` свойство пакета при импорте или экспорте пакета. Если сохранение пакета производится с помощью мастера импорта и экспорта [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], то можно также изменить свойство `ProtectionLevel`.  
  
### <a name="to-set-or-change-the-protection-level-of-a-package-in-sql-server-data-tools"></a>Установка или изменение уровня защиты пакета в SQL Server Data Tools  
  
1.  Просмотрите доступные значения для `ProtectionLevel` свойства в разделе [Установка уровня защиты пакетов](security/access-control-for-sensitive-data-in-packages.md)и выберите подходящее значение для пакета.  
  
2.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий пакет.  
  
3.  Откройте пакет в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
4.  Если свойства пакета не отображаются в окне свойств, щелкните область конструктора.  
  
5.  В окне «Свойства» в **безопасности** группу, выберите соответствующее значение для `ProtectionLevel` свойства.  
  
     Если выбран уровень защиты, для которого требуется пароль, введите пароль в качестве значения свойства **PackagePassword** .  
  
6.  Чтобы сохранить пакет, в меню **Файл** выберите пункт **Сохранить выбранные элементы** .  
  
### <a name="to-set-or-change-the-protection-level-of-packages-at-the-command-prompt"></a>Установка или изменение уровня защиты пакетов в командной строке  
  
1.  Просмотрите доступные значения для `ProtectionLevel` свойства в разделе [Установка уровня защиты пакетов](security/access-control-for-sensitive-data-in-packages.md)и выберите подходящее значение для пакета.  
  
2.  Просмотрите сопоставления для `Encrypt` параметр в разделе [dtutil Utility](dtutil-utility.md)и определить соответствующее целое число, которое используется в качестве значения выбранного `ProtectionLevel` свойство.  
  
3.  Откройте окно командной строки.  
  
4.  В командной строке перейдите к папке, содержащей пакет или пакеты, для которых требуется задать `ProtectionLevel` свойства.  
  
     В примерах синтаксиса в следующем шаге предполагается, что эта папка является текущей папкой.  
  
5.  Установите или измените уровень защиты пакета или пакетов при помощи команды, подобно показанной в одном из следующих примеров.  
  
    -   Следующая команда задает `ProtectionLevel` свойства отдельного пакета в файловой системе равным уровню 2 – «Шифровать конфиденциальные данные паролем», с паролем «strongpassword»:  
  
         `dtutil.exe /file "C:\Package.dtsx" /encrypt file;"C:\Package.dtsx";2;strongpassword`  
  
    -   Следующая команда задает свойство `ProtectionLevel` всех пакетов в определенной папке файловой системы равным уровню 2 – «Шифровать конфиденциальные данные паролем» с паролем «strongpassword»:  
  
         `for %f in (*.dtsx) do dtutil.exe /file %f /encrypt file;%f;2;strongpassword`  
  
         Если подобную команду использовать в пакетном файле, то в него необходимо включить заполнитель «%f» в виде «%%f».  
  
## <a name="see-also"></a>См. также  
 [Программа dtutil](dtutil-utility.md)  
  
  