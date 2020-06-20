---
title: Руководство. Установка советника по переходу | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, installing
- Upgrade Advisor [SQL Server], installing
ms.assetid: 481b0704-ce79-4543-b141-67306128aa2b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ac1488cd9a42a8f7e212fe533615dbb131fe7290
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059305"
---
# <a name="how-to-install-upgrade-advisor"></a>Установка помощника по обновлению
  Помощник по обновлению поддерживает удаленный анализ всех поддерживаемых компонентов, за исключением служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Если просмотр экземпляров служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не производится, помощник по обновлению может быть установлен на любой компьютер, который способен установить соединение с требуемым экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Компьютер также должен удовлетворять необходимым условиям для установки помощника по обновлению. Для просмотра экземпляров служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]следует установить помощник по обновлению на сервер отчетов.  
  
 Дополнительные сведения см. в разделе [Установка помощника по обновлению](../../../2014/sql-server/install/installing-upgrade-advisor.md).  
  
### <a name="to-install-upgrade-advisor"></a>Установка помощника по обновлению  
  
1.  Запустите установку одним из следующих методов.  
  
    -   Если выполняется установка с [!INCLUDE[msCoName](../../includes/msconame-md.md)] веб-сайта, щелкните ссылку для **скачивания** и нажмите кнопку **выполнить** , чтобы начать установку.  
  
    -   Если выполняется установка с носителя продукта, откройте папку **Redist** , откройте папку **советника по переходу** , а затем дважды щелкните **SQLUA.msi**.  
  
    > [!NOTE]  
    >  Для удаления советника по переходу необходима платформа [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 4. Если платформа не установлена или установлена ее предварительная версия, будет выдано сообщение об ошибке. Сначала удалите все предыдущие версии платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], а затем установите последнюю версию платформы .NET Framework 4.  
    >   
    >  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom является необходимым условием для установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] помощника по обновлению и не устанавливается программой установки помощника по обновлению. Для установки необходимо загрузить и установить [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom из [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] пакета дополнительных компонентов.  
  
2.  На странице **Добро пожаловать на страницу [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] установки советника по переходу** нажмите кнопку **Далее**.  
  
3.  На странице Лицензионное **соглашение** прочтите лицензионное соглашение. Если вы согласны, установите флажок **я принимаю условия лицензионного соглашения** и нажмите кнопку **Далее**.  
  
4.  На странице **сведения о регистрации** введите свое имя и название компании.  
  
5.  На странице **Выбор компонентов** проверьте значение параметра **путь установки** . При необходимости используйте кнопку **Обзор** , чтобы изменить расположение. Щелкните **Далее**.  
  
6.  На странице **все готово для установки программы** нажмите кнопку **установить** , чтобы установить советник по переходу.  
  
7.  Нажмите кнопку **Готово**, чтобы закрыть мастер.  
  
## <a name="see-also"></a>См. также:  
 [Компоненты, необходимые для помощника по обновлению](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)  
  
  
