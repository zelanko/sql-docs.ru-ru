---
title: Подключение к службе хранилища Microsoft Azure
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.windowsazurestorage.connect.f1
- SQL13.SWB.WINDOWSAZURESTORAGE.CONNECT.F1
ms.assetid: ''
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 07/12/2017
ms.openlocfilehash: f88bafe27da30ceec6154bf64cd9ced0046f7e87
ms.sourcegitcommit: d855def79af642233cbc3c5909bc7dfe04c4aa23
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2020
ms.locfileid: "87123085"
---
# <a name="connect-to-microsoft-azure-storage"></a>Подключение к службе хранилища Microsoft Azure

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Диалоговое окно **Соединение службы хранилища Azure** позволяет указать учетную запись хранения и проверить соединение с Azure.  
  
## <a name="options"></a>Параметры  
Укажите следующие сведения об учетной записи Azure и нажмите кнопку **Далее** для продолжения.  
  
1.  **Учетная запись хранения** — укажите имя учетной записи хранения.

   >[!NOTE]
   > Вы можете подключаться только к [учетным записям хранения общего назначения](https://docs.microsoft.com/azure/storage/common/storage-introduction#azure-storage-services). Подключение к другим типам учетных записей хранилища может привести к такой ошибке:
   >
   >  Значение одного из заголовков HTTP имеет неправильный формат. (Microsoft.SqlServer.StorageClient).
   >
   >  Удаленный сервер вернул ошибку: (400) Неправильный запрос. (System)

2.  **Ключ учетной записи** — укажите ключ учетной записи для указанной учетной записи хранения.  
  
3.  **Использовать защищенные конечные точки (HTTPS)**  — параметр позволяет использовать зашифрованное соединение и безопасный способ идентификации для сетевого веб-сервера.  
  
4.  **Сохранить ключ учетной записи** — параметр позволяет сохранить пароль в зашифрованном файле.  
  
