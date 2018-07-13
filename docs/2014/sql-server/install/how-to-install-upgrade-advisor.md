---
title: 'Как: установить помощник по обновлению | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, installing
- Upgrade Advisor [SQL Server], installing
ms.assetid: 481b0704-ce79-4543-b141-67306128aa2b
caps.latest.revision: 24
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 241bae15e3d4edf548e12cfcb06ca09cab8c8a89
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37216444"
---
# <a name="how-to-install-upgrade-advisor"></a>Как: установить помощник по обновлению
  Помощник по обновлению поддерживает удаленный анализ всех поддерживаемых компонентов, за исключением служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Если просмотр экземпляров служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не производится, помощник по обновлению может быть установлен на любой компьютер, который способен установить соединение с требуемым экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Компьютер также должен удовлетворять необходимым условиям для установки помощника по обновлению. Для просмотра экземпляров служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]следует установить помощник по обновлению на сервер отчетов.  
  
 Дополнительные сведения см. в разделе [Installing Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md).  
  
### <a name="to-install-upgrade-advisor"></a>Установка помощника по обновлению  
  
1.  Запустите установку одним из следующих методов.  
  
    -   При установке из [!INCLUDE[msCoName](../../includes/msconame-md.md)] веб-сайт, щелкните **загрузить** ссылку, а затем нажмите кнопку **запуска** кнопку, чтобы начать установку.  
  
    -   При установке с носителя продукта, откройте **redist** откройте **помощник по обновлению** папку и дважды щелкните **SQLUA.msi**.  
  
    > [!NOTE]  
    >  Для удаления советника по переходу необходима платформа [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 4. Если платформа не установлена или установлена ее предварительная версия, будет выдано сообщение об ошибке. Сначала удалите все предыдущие версии платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], а затем установите последнюю версию платформы .NET Framework 4.  
    >   
    >  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom является необходимым условием для установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] помощника по обновлению и не устанавливается программой установки помощника по обновлению. Программа установки потребует загрузить и установить [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom из [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] пакета дополнительных компонентов.  
  
2.  На **приветствует [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] помощника по обновлению** щелкните **Далее**.  
  
3.  На **лицензионное соглашение** страницы, прочтите лицензионное соглашение. Если вы согласны, установите **я принимаю условия лицензионного соглашения** и нажмите кнопку **Далее**.  
  
4.  На **сведения о регистрации** введите имя и организацию.  
  
5.  На **Выбор компонентов** просмотрите **путь установки** значение. При необходимости используйте **Обзор** кнопку, чтобы изменить расположение. Нажмите кнопку **Далее**.  
  
6.  На **все готово для установки программы** щелкните **установить** установки помощника по обновлению.  
  
7.  Чтобы завершить работу мастера, нажмите кнопку **Готово** .  
  
## <a name="see-also"></a>См. также  
 [Компоненты, необходимые для помощника по обновлению](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)  
  
  
