---
title: Подключение к службе хранилища Microsoft Azure
ms.custom: seo-lt-2019
ms.date: 07/12/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.windowsazurestorage.connect.f1
- SQL13.SWB.WINDOWSAZURESTORAGE.CONNECT.F1
ms.assetid: ''
author: markingmyname
ms.author: maghan
ms.openlocfilehash: eb943430136a1406ea18b9c387c98fbec6fd27cf
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75245016"
---
# <a name="connect-to-microsoft-azure-storage"></a>Подключение к службе хранилища Microsoft Azure
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Диалоговое окно **Соединение службы хранилища Azure** позволяет указать учетную запись хранения и проверить соединение с Azure.  
  
## <a name="options"></a>Параметры  
Укажите следующие сведения об учетной записи Azure и нажмите кнопку **Далее** для продолжения.  
  
1.  **Учетная запись хранения** — укажите имя учетной записи хранения.

   >[!NOTE]
   > Вы можете подключаться только к [учетным записям хранения общего назначения](https://docs.microsoft.com/azure/storage/storage-introduction#azure-storage-services). Подключение к другим типам учетных записей хранилища может привести к такой ошибке:
   >
   >  Значение одного из заголовков HTTP имеет неправильный формат. (Microsoft.SqlServer.StorageClient).
   >
   >  Удаленный сервер вернул ошибку: (400) Неправильный запрос. (System)

2.  **Ключ учетной записи** — укажите ключ учетной записи для указанной учетной записи хранения.  
  
3.  **Использовать защищенные конечные точки (HTTPS)**  — параметр позволяет использовать зашифрованное соединение и безопасный способ идентификации для сетевого веб-сервера.  
  
4.  **Сохранить ключ учетной записи** — параметр позволяет сохранить пароль в зашифрованном файле.  
  
