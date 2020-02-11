---
title: Установка обновлений из командной строки | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: bc98ba2b-aae9-4d01-aa85-d4c36428cb0b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 51ad82519e8afd5e4a871046465e0cafec2f783e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62774988"
---
# <a name="installing-updates-from-the-command-prompt"></a>Установка обновлений из командной строки
  Проверьте скрипты установки и доработайте их в соответствии с задачами организации.  
  
## <a name="sample-syntax-for-installation"></a>Образец синтаксиса для программы установки  
 Имя пакета может быть разным и включает обозначение языка, выпуска и архитектуры процессора. Применение обновления из командной строки. Замените <имя_пакета> именем конкретного пакета обновления:  
  
-   Обновление одного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и всех общих компонентов, таких как службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и средства управления: экземпляр можно указать с помощью параметра InstanceName или InstanceID. Чтобы обновить подготовленный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], необходимо указать параметр InstanceID <имя_пакета>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /InstanceName=MyInstance или <имя_пакета>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /InstanceID=\<Instance ID>.  
  
-   Программа установки может интегрировать последние обновления продукта в основную установку продукта, чтобы он и применимые обновления устанавливались одновременно. Можно подготовить установку экземпляра ядра СУБД, включающую обновление продукта: setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=PrepareImage /UpdateEnabled=True /UpdateEnabled=True /UpdateSource=\<путь, откуда скачивается обновление> /INSTANCEID=\<Instance ID>/FEATURES=SQLEngine.  
  
-   Обновление только общих компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], таких как [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и средства управления: <имя_пакета>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch  
  
-   Обновление всех экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на компьютере и всех общих компонентов, таких как [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и средства управления: <имя_пакета>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /AllInstances.  
  
 Удаление обновления из командной строки. Замените <имя_пакета> именем конкретного пакета обновления.  
  
-   Удаление обновления из одного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и всех общих компонентов, таких как [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и средства управления: <имя_пакета>.exe /qs /Action=RemovePatch /InstanceName=MyInstance.  
  
-   Удаление обновления только из общих компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], таких как службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и средства управления: <имя_пакета>.exe /qs /Action=RemovePatch  
  
    > [!NOTE]  
    >  Установщик обновлений поддерживает версию общих компонентов такой же или более поздней, чем версия экземпляра, на самом высоком уровне.  
  
## <a name="supported-command-prompt-parameters"></a>Поддерживаемые параметры командной строки  
  
> [!IMPORTANT]  
>  При возможности указывайте учетные данные безопасности в среде выполнения. Если нужно хранить учетные данные в файле скрипта, для этого файла необходимо обеспечить защиту, чтобы исключить несанкционированный доступ.  
  
|Параметр|Description|  
|------------|-----------------|  
|**/?**|Отображает справку командной строки для автоматической установки|  
|**/action=Patch или /action=RemovePatch**|Задает действие установки: Patch или RemovePatch.|  
|**/allinstances**|Устанавливает обновление [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для всех экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и всех общих компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не привязанных к экземпляру.|  
|**/instanceName = instanceName** <sup>1</sup>|Устанавливает обновление [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с именем InstanceName и всех общих компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не привязанных к экземпляру.|  
|**/InstanceID=Inst1**|Применяет обновление [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с именем «Inst1» и всех общих компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не привязанных к экземпляру.|  
|**/quiet**|Запускает программу установки обновления для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в автоматическом режиме.|  
|**/qs**|Отображается только диалоговое окно выполнения.|  
|**/UpdateEnabled**|Задает, должна ли программа установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаруживать и включать обновления продукта. Допустимые значения — True и False либо 1 и 0. По умолчанию программа установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет включать найденные обновления.|  
|**/IAcceptSQLServerLicenseTerms**|Требуется только в том случае, если для автоматической установки указан параметр /Q или /QS.|  
  
 <sup>1</sup> этот параметр нельзя указать, чтобы применить обновление к подготовленному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Вместо этого необходимо указать параметр /instanceID.  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения об обслуживании установки SQL Server](../../sql-server/install/overview-of-sql-server-servicing-installation.md)  
  
  
