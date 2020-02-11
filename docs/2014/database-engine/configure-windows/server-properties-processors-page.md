---
title: Свойства сервера (страница "Процессоры") | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.processor.f1
ms.assetid: cc1581a2-492b-41f0-bda5-17909b65c4f7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: aae800226a585f7a29334887829be2a09277a004
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62809280"
---
# <a name="server-properties-processors-page"></a>Свойства сервера (страница «Процессоры»)
  Используйте эту страницу, чтобы просмотреть или изменить параметры процессоров. Настройки соответствия процессоров доступны только в случае, если в системе установлено более одного процессора.  
  
## <a name="options"></a>Параметры  
 **Соответствие процессоров**  
 Связывает процессоры с определенными потоками, чтобы устранить чрезмерную нагрузку на процессоры и уменьшить количество переходов потоков между процессорами. Дополнительные сведения см. в разделе [Параметр конфигурации сервера "affinity mask"](affinity-mask-server-configuration-option.md).  
  
 **Сходство ввода-вывода**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Привязывает дисковые операции ввода-вывода к заданному подмножеству ЦП. Дополнительные сведения см. в разделе [Параметр конфигурации сервера "affinity Input-Output mask"](affinity-input-output-mask-server-configuration-option.md).  
  
 **Автоматически устанавливать маску схожести процессоров для всех процессоров**  
 Позволяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливать соответствие процессоров.  
  
 **Автоматически устанавливать маску схожести ввода-вывода для всех процессоров**  
 Позволяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливать привязку ввода-вывода.  
  
 **Максимальное число рабочих потоков**  
 Значение 0 позволяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливать количество потоков исполнителя динамически. Эта настройка является наиболее подходящей для большинства систем. Однако в зависимости от конфигурации системы, присвоение этому параметру определенного значения иногда улучшает производительность. Дополнительные сведения см. в статье [Настройка параметра конфигурации сервера max worker threads](configure-the-max-worker-threads-server-configuration-option.md).  
  
 **Повышение приоритета SQL Server**  
 Указывает, следует ли [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выставить более высокий приоритет планирования [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows по сравнению с другими процессами на том же компьютере. Дополнительные сведения см. в статье [Настройка параметра конфигурации сервера priority boost](configure-the-priority-boost-server-configuration-option.md).  
  
 **Использовать волокна Windows (использование упрощенных пулов)**  
 Использовать легковесные потоки (волокна) Windows вместо обычных потоков для службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Обратите внимание на то, что такая возможность доступна только в Windows 2003 Server Edition. Дополнительные сведения см. в разделе [Параметр конфигурации сервера «использование упрощенных пулов»](lightweight-pooling-server-configuration-option.md).  
  
 **Настроенные значения**  
 Отображает настроенные значения для параметров на этой панели. В случае изменения этих значений выберите пункт **Текущие значения** и посмотрите, вступили ли в силу внесенные изменения. В противном случае первым должен быть перезапущен экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Выполняемые значения**  
 Просмотр текущих значений для параметров на этой панели. Эти значения доступны только для чтения.  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)  
  
  
