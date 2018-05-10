---
title: Подключение к службе хранилища Microsoft Azure (восстановление)| Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.suite: sql
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.restore.connectstorage.f1
ms.assetid: c0b7d7c8-b878-4b7f-8120-d0c6917b583f
caps.latest.revision: 6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e1c0ef03df12e05fb869155b94dce13865ad70ac
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="connect-to-microsoft-azure-storage-restore"></a>Подключение к службе хранилища Microsoft Azure (восстановление)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Это диалоговое окно позволяет указать сведения для подключения к учетной записи хранения Windows Azure для получения файлов в учетной записи хранения. После ввода необходимой информации нажмите кнопку **Подключить** , чтобы установить соединение с хранилищем Windows Azure.  
  
## <a name="windows-azure-storage-account"></a>Учетная запись хранения Windows Azure  
 **Учетная запись хранения**  
 Выберите, введите или вставьте имя учетной записи хранения Windows Azure. В раскрывающемся списке указаны ранее используемые учетные записи.  
  
 **Ключ учетной записи**  
 Укажите ключ доступа к учетной записи хранения Windows Azure.  
  
 Флажок**Использовать защищенные конечные точки (HTTPS)**   
 Установите этот флажок, чтобы установить безопасное соединение с хранилищем Windows Azure — рекомендуется.  
  
 Флажок**Сохранить мой ключ учетной записи**   
 Установите этот флажок, чтобы SQL Server запоминал ключ доступа для этой учетной записи хранения.  
  
### <a name="sql-credential"></a>Учетные данные SQL  
 **Выбор существующих учетных данных**  
 Выберите существующие учетные данные SQL, соответствующие учетной записи хранения и ключу доступа.  
  
 **Создание новых учетных данных**  
 Выберите этот параметр, чтобы создать новые учетные данные, используя учетную запись хранения и ключ доступа. Введите имя учетных данных в поле **Имя учетных данных** .  
  
  
