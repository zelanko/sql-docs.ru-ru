---
title: Выбор диска кластера | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cluster disk selection
ms.assetid: 0d6b863d-5972-4a20-9990-64ee8016fea6
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ce08658fe769a356e4cd24e29ed094692892e48f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100140"
---
# <a name="cluster-disk-selection"></a>Выбор диска кластера
  Страница **Выбор диска кластера** мастера установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется для выбора диска кластера как общего ресурса для отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будут размещены на этом диске кластера.  
  
 Общий диск кластера не является обязательным для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] установок кластера. Файловый сервер SMB является поддерживается в качестве хранилища для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] перехода на другой ресурс установок кластера и может быть указан с помощью **ядро СУБД — каталоги данных** перед завершением установки.  
  
> [!WARNING]  
>  Если для установки были выбраны службы Analysis Services, необходимо указать общий диск кластера.  
>   
>  Если на этом экземпляре отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] планируется включить параметр FILESTREAM, необходимо указать общий диск кластера.  
  
## <a name="options"></a>Параметры  
 **Общие диски**  
 Выбирает диск из списка. Данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будут размещены на этом диске кластера.  
  
 Можно указать только один диск. Если выбрать группу, содержащую ресурс кластерного кворума, выводится предупреждение. Рекомендуется не выполнять установку на ресурс кластерного кворума.  
  
 **Доступные общие диски**  
 Отображает список доступных дисков, указывает, определен ли отдельный диск как общий, и выводит описание дискового ресурса.  
  
  