---
title: Установка или изменение уровня защиты пакетов | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- passwords [Integration Services]
- packages [Integration Services],security
- security [Integration Services],protection levels
- protection level for packages [Integration Services]
ms.assetid: 904a5580-82ba-4a26-b0c5-d1c989975f61
author: janinezhang
ms.author: janinez
ms.openlocfilehash: bcb8f4da5f39647665b3f07355ea8eed2506cda5
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84963414"
---
# <a name="set-or-change-the-protection-level-of-packages"></a>Установка и изменение уровня защиты пакетов
  Для управления доступом к содержимому пакетов и конфиденциальным данным в них, таким как пароли, необходимо задать значение свойства `ProtectionLevel`. Пакеты, которые содержатся в проекте, должны обладать тем же уровнем защиты, что и сам проект. Это необходимо для создания проекта. При изменении настройки свойства `ProtectionLevel` в проекте потребуется вручную обновить настройку свойства для пакетов.  
  
 Сведения о том, как определить `ProtectionLevel` Параметры, подходящие для пакетов на разных этапах жизненного цикла пакета, см. в разделе [Управление доступом для конфиденциальных данных в пакетах](security/access-control-for-sensitive-data-in-packages.md). Общие сведения о средствах безопасности в службах [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] см. в разделе [Общие сведения о безопасности (службы Integration Services)](security/security-overview-integration-services.md).  
  
 В приведенной в данном разделе процедуре описано использование [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] или средства командной dtutil для изменения свойства `ProtectionLevel`.  
  
> [!NOTE]  
>  В дополнение к приведенной в этом разделе процедуре можно, как правило, задать или изменить свойство пакета `ProtectionLevel` при импорте или экспорте пакета. Если сохранение пакета производится с помощью мастера импорта и экспорта [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], то можно также изменить свойство `ProtectionLevel`.  
  
### <a name="to-set-or-change-the-protection-level-of-a-package-in-sql-server-data-tools"></a>Установка или изменение уровня защиты пакета в SQL Server Data Tools  
  
1.  Проверьте доступные значения `ProtectionLevel` свойства в разделе [Настройка уровня защиты пакетов](security/access-control-for-sensitive-data-in-packages.md)и определите соответствующее значение для пакета.  
  
2.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий пакет.  
  
3.  Откройте пакет в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
4.  Если свойства пакета не отображаются в окне свойств, щелкните область конструктора.  
  
5.  В окно свойств в группе **Безопасность** выберите соответствующее значение для `ProtectionLevel` Свойства.  
  
     Если выбран уровень защиты, для которого требуется пароль, введите пароль в качестве значения свойства **PackagePassword** .  
  
6.  Чтобы сохранить пакет, в меню **Файл** выберите пункт **Сохранить выбранные элементы** .  
  
### <a name="to-set-or-change-the-protection-level-of-packages-at-the-command-prompt"></a>Установка или изменение уровня защиты пакетов в командной строке  
  
1.  Проверьте доступные значения `ProtectionLevel` свойства в разделе [Настройка уровня защиты пакетов](security/access-control-for-sensitive-data-in-packages.md)и определите соответствующее значение для пакета.  
  
2.  Проверьте сопоставления для `Encrypt` параметра в разделе [программа dtutil](dtutil-utility.md)и определите соответствующее целое число, которое будет использоваться в качестве значения выбранного `ProtectionLevel` Свойства.  
  
3.  Откройте окно командной строки и  
  
4.  В командной строке перейдите к папке с пакетом или пакетами, для которых требуется задать свойство `ProtectionLevel`.  
  
     В примерах синтаксиса в следующем шаге предполагается, что эта папка является текущей папкой.  
  
5.  Установите или измените уровень защиты пакета или пакетов при помощи команды, подобно показанной в одном из следующих примеров.  
  
    -   Следующая команда задает свойство `ProtectionLevel` отдельного пакета в файловой системе равным уровню 2 – «Шифровать конфиденциальные данные паролем» с паролем «strongpassword»:  
  
         `dtutil.exe /file "C:\Package.dtsx" /encrypt file;"C:\Package.dtsx";2;strongpassword`  
  
    -   Следующая команда задает свойство `ProtectionLevel` всех пакетов в определенной папке файловой системы равным уровню 2 – «Шифровать конфиденциальные данные паролем» с паролем «strongpassword»:  
  
         `for %f in (*.dtsx) do dtutil.exe /file %f /encrypt file;%f;2;strongpassword`  
  
         Если подобную команду использовать в пакетном файле, то в него необходимо включить заполнитель «%f» в виде «%%f».  
  
## <a name="see-also"></a>См. также:  
 [Программа dtutil](dtutil-utility.md)  
  
  
