---
author: MikeRayMSFT
ms.prod: sql
ms.technology: big-data-cluster
ms.topic: include
ms.date: 06/22/2020
ms.author: mikeray
ms.openlocfilehash: b72f8044638adbf75049392fae32447a8a749a6d
ms.sourcegitcommit: d973b520f387b568edf1d637ae37d117e1d4ce32
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85215172"
---
Начиная с SQL Server 2019 CU5, при развертывании нового кластера с обычной проверкой подлинности все конечные точки, включая шлюз, используют `AZDATA_USERNAME` и `AZDATA_PASSWORD`. Конечные точки в кластерах, обновленных до CU5, продолжают использовать `root` в качестве имени пользователя для подключения к конечной точке шлюза. Это изменение не применяется к развертываниям, в которых используется проверка подлинности с помощью Active Directory. Подробные сведения см. в заметках о выпуске в разделе [Учетные данные для доступа к службам через конечную точку шлюза](../big-data-cluster/release-notes-big-data-cluster.md#credentials-for-accessing-services-through-gateway-endpoint).