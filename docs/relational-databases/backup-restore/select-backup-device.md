---
title: Выбор устройства резервного копирования | Документация Майкрософт
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
- sql13.swb.selectbackupdevice.f1
ms.assetid: 7887c9fd-15ce-4cc8-b069-845c1d09088c
caps.latest.revision: 27
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c743a249373317a83096c311916a94d7e68607d3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="select-backup-device"></a>Выбор устройства резервного копирования
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Используйте диалоговое окно **Выбор устройства резервного копирования** , чтобы выбрать логическое устройство резервного копирования для операции восстановления.  
  
 Логическим устройством резервного копирования является определяемое пользователем логическое устройство, которое относится к физическим устройствам, или ленточный накопитель, или дисковый накопитель, предоставляемый операционной системой.  
  
> [!NOTE]  
>  Если несколько устройств резервного копирования используется для выполнения операции резервного копирования, все они должны соответствовать одному типу устройства.  
  
 **Использование среды SQL Server Management Studio для просмотра содержимого устройства резервного копирования**  
  
-   [Просмотр содержимого ленты или файла резервной копии (SQL Server)](../../relational-databases/backup-restore/view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [Просмотр свойств и содержимого логического устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a>Параметры  
 **устройство резервного копирования;**  
 В окне списка выберите имя устройства резервного копирования, с которого необходимо произвести восстановление.  
  
 Сведения о просмотре содержимого устройства резервного копирования см. в разделе [Просмотр свойств и содержимого логического устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md).  
  
## <a name="remarks"></a>Remarks  
 Если не отображается логическое устройство резервного копирования, содержащее необходимую резервную копию, резервная копия может быть записана прямо на один или более дисковых накопителей или ленточных накопителей. В таком случае закройте диалоговое окно **Выбор устройства резервного копирования** и в диалоговом окне **Указание резервной копии** выберите **Файл** или **Лента** в окне списка **Носитель резервной копии** .  
  
## <a name="see-also"></a>См. также:  
 [Устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/backup-devices-sql-server.md)  
  
  
