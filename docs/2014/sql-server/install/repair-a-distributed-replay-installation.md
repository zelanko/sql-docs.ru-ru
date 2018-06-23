---
title: Восстановление установки распределенного воспроизведения | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fcd8ca8-1ceb-457d-9545-096c74e274d7
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8adf917831b33c1603b3c0c4a1e7b678900cf7dd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179985"
---
# <a name="repair-a-distributed-replay-installation"></a>Восстановление установки распределенного воспроизведения
  При восстановлении компонента распределенного воспроизведения (контроллера или клиента) выполняется следующее.  
  
1.  Повторная установка всех связанных файлов на диске с заменой существующих файлов.  
  
2.  Повторное создание учетной записи службы Windows, если соответствующая учетная запись службы была удалена.  
  
 Нельзя использовать операцию восстановления для добавления или удаления компонентов. Чтобы добавить или удалить компонент, установите или снимите флажок напротив него в дереве компонентов на странице **Выбор компонентов** в программе установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="to-repair-a-failed-installation-of-distributed-replay"></a>Восстановление установки распределенного воспроизведения, завершившейся ошибкой  
  
1.  В меню **Пуск** выберите **Панель управления**, а затем дважды щелкните пункт **Установка и удаление программ**.  
  
2.  Выберите [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] в окне **Удаление или изменение программы** и нажмите в диалоговом окне [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] кнопку **Восстановить**.  
  
3.  Следуйте инструкциям мастера [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и на странице **Выбор компонентов** выберите компоненты распределенного воспроизведения, которые необходимо восстановить, затем нажмите кнопку **Далее**.  
  
4.  Завершите мастер установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] для восстановления выбранных компонентов программы распределенного воспроизведения.  
  
  