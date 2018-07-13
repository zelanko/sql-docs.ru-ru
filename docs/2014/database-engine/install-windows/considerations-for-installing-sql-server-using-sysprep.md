---
title: Вопросы по установке SQL Server с помощью SysPrep | Документы Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e1792eeb-2874-4653-b20e-3063f4eb4e5d
caps.latest.revision: 21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 140fac99176fc41f5e3967c158c7929fe9554989
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37180421"
---
# <a name="considerations-for-installing-sql-server-using-sysprep"></a>Вопросы по установке SQL Server с помощью SysPrep
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep позволяет подготавливать отдельные экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на компьютере и завершать настройку позднее. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep для настройки отдельного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]применяется процесс, состоящий из двух действий. Эти действия включают следующие шаги.  
  
-   [Подготовка образа](#BKMK_PrepareImage)  
  
     На этом шаге процесс установки останавливается после установки двоичных файлов продукта без настройки компьютера, сети или информации, связанной только с определенным подготавливаемым экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   [Завершение создания образа](#BKMK_CompleteImage)  
  
     На этом шаге завершается настройка подготовленного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При его выполнении можно задать информацию, связанную только с определенным компьютером, сетью или учетной записью.  
  
 Дополнительные сведения об установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью SysPrep см. в разделе [Установка SQL Server 2014 с помощью SysPrep](install-sql-server-using-sysprep.md).  
  
## <a name="common-uses-for-includessnoversionincludesssnoversion-mdmd-sysprep"></a>Распространенные варианты применения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep  
 Функцию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep можно использовать одним из следующих способов.  
  
-   На шаге подготовки образа можно подготовить один или несколько ненастроенных экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на одном компьютере. Эти подготовленные экземпляры можно настроить на шаге завершения создания образа на том же компьютере.  
  
-   Можно захватить файл конфигурации программы установки подготавливаемого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и использовать его для последующей настройки при подготовке других ненастроенных экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на нескольких компьютерах.  
  
-   Совместно со средством Windows System Preparation (также называемым Windows SysPrep) можно создать образ операционной системы, включая ненастроенный подготовленный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на первоначальном компьютере. Затем можно выполнить развертывание этого образа операционной системы на нескольких компьютерах. После завершения настройки операционной системы подготовленные экземпляры можно настроить на шаге «Завершение создания образа» в программе установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     Средство Windows SysPrep служит для подготовки образов операционной системы. Оно используется для получения настроенного образа операционной системы, готового к развертыванию в пределах всей организации. Дополнительные сведения о программе SysPrep и работе с ней см. в разделе [Что такое SysPrep](http://go.microsoft.com/fwlink/?LinkId=143546).  
  
## <a name="installation-media-considerations"></a>Рекомендации при работе с установочными носителями  
 Если используется полная версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то необходимо учитывать следующие моменты.  
  
-   Выпуски [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](кроме Express)  
  
    -   Для установки двоичных файлов продукта на шаге подготовки образа используется выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Evaluation Edition. После завершения создания экземпляра выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] зависит от идентификатора продукта, указанного на шаге завершения создания образа.  
  
    -   Если указан идентификатор продукта Evaluation Edition, то устанавливается срок оценки 180 дней с момента завершения создания подготавливаемого экземпляра.  
  
-   Выпуски [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Express  
  
    -   Для подготовки экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Edition пользуйтесь установочным носителем Express.  
  
    -   Нельзя указать идентификатор продукта для подготавливаемого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Edition.  
  
## <a name="supported-includessnoversionincludesssnoversion-mdmd-installations"></a>Поддерживаемые установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SysPrep поддерживаются все функции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], включая средства.  
  
 Можно подготовить несколько экземпляров для параллельной установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] или более ранних версий. Компоненты данных экземпляров должны поддерживать SysPrep.  
  
 Собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливается и создается автоматически при завершении шага подготовки образа.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и модуль записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подготавливаются автоматически при подготовке экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Они создаются по окончании создания экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на шаге завершения создания образа.  
  
 Сведения о поддерживаемых выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [функции, поддерживаемые различными выпусками SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 Во время настройки подготовленного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]можно выполнить обновление выпусков. Этот параметр не поддерживается для выпусков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.  
  
 Начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep поддерживает установки кластера отработки отказа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из командной строки.  
  
## <a name="includessnoversionincludesssnoversion-mdmd-sysprep-limitations"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep  
 Восстановление подготавливаемого экземпляра не поддерживается. При возникновении ошибки в работе программы установки во время подготовки образа или завершения его создания необходимо запустить мастер удаления.  
  
##  <a name="BKMK_PrepareImage"></a> Подготовка образа  
 На шаге подготовки образа выполняется установка продукта и компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , но не выполняется настройка установки.  
  
 В рамках этого действия можно выбрать компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для установки и указать расположение для установки файлов продукта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно подготовить либо путем выбора пункта **Подготовка образа изолированного экземпляра для развертывания SysPrep** на странице **Дополнительно** в **Центре установки** , либо с помощью командной строки.  
  
-   На одном компьютере можно подготовить несколько экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , создание которых будет завершено позднее.  
  
-   Можно добавить или удалить компоненты, поддерживаемые для установки SysPrep из существующих подготовленных экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 После завершения подготовки экземпляра в меню **Пуск** появляется ярлык, который служит для завершения настройки подготовленного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
##  <a name="BKMK_CompleteImage"></a> Завершение создания образа  
 Завершение создания подготовленного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется одним из следующих методов.  
  
-   с помощью ярлыка в меню «Пуск»;  
  
-   переход к шагу **Завершение образа подготовленного изолированного экземпляра** на странице **Дополнительно** в **Центре установки**.  
  
## <a name="see-also"></a>См. также  
 [Планирование установки SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)  
  
  
