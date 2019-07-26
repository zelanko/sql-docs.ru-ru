---
ms.openlocfilehash: 2dc81d434714e0a13912fa6f14e1194df5e5afe3
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68215608"
---
> [!NOTE]
> При создании ресурса и периодически после этого агент ресурсов Pacemaker автоматически задает в группе доступности значение `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` на основе ее конфигурации. Например, если группа доступности содержит три синхронные реплики, агент задаст для `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` значение `1`. Дополнительную информацию и параметры конфигурации см. в разделе [High Availability and Data Protection for Availability Group Configurations](../linux/sql-server-linux-availability-group-ha.md) (Высокий уровень доступности и защита данных для конфигураций групп доступности). 