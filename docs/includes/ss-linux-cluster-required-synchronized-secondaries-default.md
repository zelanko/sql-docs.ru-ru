---
ms.openlocfilehash: 2dc81d434714e0a13912fa6f14e1194df5e5afe3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68215608"
---
> [!NOTE]
> При создании ресурса и периодически после этого агент ресурсов Pacemaker автоматически задает в группе доступности значение `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` на основе ее конфигурации. Например, если группа доступности содержит три синхронные реплики, агент задаст для `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` значение `1`. Дополнительную информацию и параметры конфигурации см. в разделе [Высокий уровень доступности и защита данных для конфигураций групп доступности](../linux/sql-server-linux-availability-group-ha.md). 