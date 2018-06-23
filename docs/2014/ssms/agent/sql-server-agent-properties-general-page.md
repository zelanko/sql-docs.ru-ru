---
title: Свойства агента SQL Server (страница "Общие") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ag.agent.general.f1
ms.assetid: b51601e9-5454-43c6-bb5e-24eb2ff043c8
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 894a9625971bd66c57449c2a87239cb5254b2d29
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087273"
---
# <a name="sql-server-agent-properties-general-page"></a>Свойства агента SQL Server (страница «Общие»)
  Эта страница используется для просмотра и изменения общих свойств службы агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="options"></a>Параметры  
 **Состояние службы**  
 Отображается текущее состояние службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Автоматический перезапуск SQL Server в случае его неожиданной остановки**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент перезапускает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при непредвиденной остановке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Автоматический перезапуск агента SQL Server в случае его неожиданной остановки**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перезапускает агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при непредвиденной остановке агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Имя файла**  
 Укажите имя файла для журнала ошибок.  
  
 **...**  
 Перейдите к файлу журнала ошибок.  
  
 **Включая трассировочные сообщения**  
 Сообщения трассировки выполнения включаются в журнал ошибок. Сообщения трассировки предоставляют подробные сведения о работе агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Поэтому при выборе этого параметра для файла журнала необходимо дополнительное место на диске. Этот параметр нужно выбирать только для устранения неполадок, связанных с агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Записать файл OEM**  
 Запись файла журнала ошибок производится не в Юникоде. Это позволяет уменьшить место на диске, необходимое для файла журнала. Однако при включении этого параметра могут возникнуть трудности с чтением сообщений, содержащих данные в Юникоде.  
  
 **Получатель для команды net send**  
 Введите имя оператора, получающего уведомления, отправленные командой net send, с сообщениями, которые агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] записывает в файл журнала.  
  
## <a name="see-also"></a>См. также  
 [Операторы](operators.md)   
 [Журнал ошибок агента SQL Server](sql-server-agent-error-log.md)  
  
  