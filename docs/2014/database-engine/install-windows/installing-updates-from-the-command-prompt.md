---
title: Установка обновлений из командной строки | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bc98ba2b-aae9-4d01-aa85-d4c36428cb0b
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5d1fb09edce06159c748be8393f8cbd46e0397b7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096495"
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
  
|Параметр|Описание|  
|------------|-----------------|  
|**/?**|Отображает справку командной строки для автоматической установки|  
|**/action=Patch или /action=RemovePatch**|Задает действие установки: Patch или RemovePatch.|  
|**/allinstances**|Устанавливает обновление [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для всех экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и всех общих компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не привязанных к экземпляру.|  
|**/ instancename = имяЭкземпляра** <sup>1</sup>|Устанавливает обновление [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с именем InstanceName и всех общих компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не привязанных к экземпляру.|  
|**/InstanceID=Inst1**|Применяет обновление [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с именем «Inst1» и всех общих компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не привязанных к экземпляру.|  
|**/quiet**|Запускает программу установки обновления для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в автоматическом режиме.|  
|**/qs**|Отображается только диалоговое окно выполнения.|  
|**/UpdateEnabled**|Задает, должна ли программа установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обнаруживать и включать обновления продукта. Допустимые значения — True и False либо 1 и 0. По умолчанию программа установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет включать найденные обновления.|  
|**/IAcceptSQLServerLicenseTerms**|Требуется только в том случае, если для автоматической установки указан параметр /Q или /QS.|  
  
 <sup>1</sup> нельзя указать этот параметр для применения обновления к подготовленному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Вместо этого необходимо указать параметр /instanceID.  
  
## <a name="see-also"></a>См. также  
 [Общие сведения об обслуживании установки SQL Server](../../sql-server/install/overview-of-sql-server-servicing-installation.md)  
  
  