---
title: "Подключение к службе хранилища Microsoft Azure | Документация Майкрософт"
ms.custom: 
ms.date: 07/12/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-f1
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.windowsazurestorage.connect.f1
- SQL13.SWB.WINDOWSAZURESTORAGE.CONNECT.F1
ms.assetid: 
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2b3f4019ad5eadcdd792586598c3cf93a4b0d1ce
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="connect-to-microsoft-azure-storage"></a>Подключение к службе хранилища Microsoft Azure
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]Диалоговое окно **Соединение хранилища Windows Azure** позволяет указать учетную запись хранилища и проверить соединение с Windows Azure.  
  
## <a name="options"></a>Параметры  
Укажите следующие сведения об учетной записи Windows Azure и нажмите кнопку **Далее** для продолжения.  
  
1.  **Учетная запись хранения** — укажите имя учетной записи хранения.

   >[!NOTE]
   > Вы можете подключаться только к [учетным записям хранения общего назначения](https://docs.microsoft.com/en-us/azure/storage/storage-introduction#introducing-the-azure-storage-services). Подключение к другим типам учетных записей хранилища может привести к такой ошибке:
   >
   >  Значение одного из заголовков HTTP имеет неправильный формат. (Microsoft.SqlServer.StorageClient).
   >
   >  Удаленный сервер вернул ошибку: (400) Неправильный запрос. (System)

2.  **Ключ учетной записи** — укажите ключ учетной записи для указанной учетной записи хранения.  
  
3.  **Использовать защищенные конечные точки (HTTPS)** — параметр позволяет использовать зашифрованное соединение и безопасный способ идентификации для сетевого веб-сервера.  
  
4.  **Сохранить ключ учетной записи** — параметр позволяет сохранить пароль в зашифрованном файле.  
  
