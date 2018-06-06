---
title: Установка обновлений из командной строки | Документы Майкрософт
ms.custom: ''
ms.date: 09/08/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: bc98ba2b-aae9-4d01-aa85-d4c36428cb0b
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 582a970eb7651db652f1b745eecef9f385dc00dd
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34771060"
---
# <a name="installing-updates-from-the-command-prompt"></a>Установка обновлений из командной строки

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Проверьте скрипты установки и доработайте их в соответствии с задачами организации. 
 
## <a name="sample-syntax-for-installation"></a>Образец синтаксиса для программы установки 
Имя пакета может быть разным и включает обозначение языка, выпуска и архитектуры процессора. Применение обновления из командной строки. Замените <имя_пакета> именем конкретного пакета обновления: 
 
- Обновление одного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и всех общих компонентов, таких как службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и средства управления: экземпляр можно указать с помощью параметра InstanceName или InstanceID. Чтобы обновить подготовленный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], нужно указать параметр InstanceID.

    ```
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /InstanceName=MyInstance
    ```
    или диспетчер конфигурации служб 
    ```
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /InstanceID=\<Instance ID>. 
    ```

- Программа установки может интегрировать последние обновления продукта в основную установку продукта, чтобы он и применимые обновления устанавливались одновременно. Можно подготовить установку экземпляра компонента Database Engine, включающую обновление продукта: 

    ```
    setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=PrepareImage /UpdateEnabled=True /UpdateSource=\<path where the update is downloaded> /INSTANCEID=\<Instance ID> /FEATURES=SQLEngine. 
    ```

- Обновление только общих компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], таких как службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и средства управления: 

    ```
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch 
    ```

- Обновление всех экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на компьютере и всех общих компонентов, таких как службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и средства управления: 

    ```
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /AllInstances. 
    ```

- Удаление обновления из отдельного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и всех общих компонентов, таких как службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и средства управления: 

    ```
    <package_name>.exe /qs /Action=RemovePatch /InstanceName=MyInstance. 
    ```

- Удаление обновления только из общих компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], таких как службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и средства управления: 

    ```
    <package_name>.exe /qs /Action=RemovePatch 
    ```

  > [!NOTE] 
  > Установщик обновлений поддерживает версию общих компонентов такой же или более поздней, чем версия экземпляра, на самом высоком уровне. 
 
## <a name="supported-parameters"></a>Поддерживаемые параметры 
 
> [!IMPORTANT] 
> При возможности указывайте учетные данные безопасности в среде выполнения. Если нужно хранить учетные данные в файле скрипта, для этого файла необходимо обеспечить защиту, чтобы исключить несанкционированный доступ. 
 
|Параметр|Описание| 
|------------|-----------------| 
|**/?**|Отображает справку командной строки для автоматической установки| 
|**/action=Patch или /action=RemovePatch**|Задает действие установки: Patch или RemovePatch.| 
|**/allinstances**|Устанавливает обновление [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для всех экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и всех общих компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не привязанных к экземпляру.| 
|**/instancename=ИмяЭкземпляра***|Устанавливает обновление [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с именем InstanceName и всех общих компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не привязанных к экземпляру.| 
|**/InstanceID=Inst1**|Применяет обновление [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с именем «Inst1» и всех общих компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не привязанных к экземпляру.| 
|**/quiet**|Запускает программу установки обновления для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в автоматическом режиме.| 
|**/qs**|Отображается только диалоговое окно выполнения.| 
|**/UpdateEnabled**|Задает, должна ли программа установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаруживать и включать обновления продукта. Допустимые значения — True и False либо 1 и 0. По умолчанию программа установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет включать найденные обновления.| 
|**/IAcceptSQLServerLicenseTerms**|Требуется только в том случае, если для автоматической установки указан параметр /Q или /QS.| 
 
 * Этот параметр нельзя указать для применения обновления к подготовленному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Вместо этого необходимо указать параметр /instanceID. 
 
## <a name="see-also"></a>См. также раздел 
 [Общие сведения об обслуживании установки SQL Server](http://msdn.microsoft.com/library/6a9fd19b-2367-4908-b638-363b1e929e1e) 
 
 
