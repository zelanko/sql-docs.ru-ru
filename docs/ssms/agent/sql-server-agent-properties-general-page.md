---
title: "Свойства агента SQL Server (страница \"Общие\") | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.ag.agent.general.f1
ms.assetid: b51601e9-5454-43c6-bb5e-24eb2ff043c8
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4046c9c45fda98646043e73c8a9b1e1bacfdd335
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="sql-server-agent-properties-general-page"></a>Свойства агента SQL Server (страница «Общие»)
Эта страница используется для просмотра и изменения общих свойств службы агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
## <a name="options"></a>Параметры  
**Состояние службы**  
Отображается текущее состояние службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
**Автоматический перезапуск SQL Server в случае его неожиданной остановки**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Агент перезапускает [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] при непредвиденной остановке [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
**Автоматический перезапуск агента SQL Server в случае его неожиданной остановки**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] перезапускает агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] при непредвиденной остановке агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
**Имя файла**  
Укажите имя файла для журнала ошибок.  
  
**...**  
Перейдите к файлу журнала ошибок.  
  
**Включая трассировочные сообщения**  
Сообщения трассировки выполнения включаются в журнал ошибок. Сообщения трассировки предоставляют подробные сведения о работе агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . Поэтому при выборе этого параметра для файла журнала необходимо дополнительное место на диске. Этот параметр нужно выбирать только для устранения неполадок, связанных с агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
**Записать файл OEM**  
Запись файла журнала ошибок производится не в Юникоде. Это позволяет уменьшить место на диске, необходимое для файла журнала. Однако при включении этого параметра могут возникнуть трудности с чтением сообщений, содержащих данные в Юникоде.  
  
**Получатель для команды net send**  
Введите имя оператора, получающего уведомления, отправленные командой net send, с сообщениями, которые агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] записывает в файл журнала.  
  
## <a name="see-also"></a>См. также:  
[Операторы](../../ssms/agent/operators.md)  
[Журнал ошибок агента SQL Server](../../ssms/agent/sql-server-agent-error-log.md)  
  
