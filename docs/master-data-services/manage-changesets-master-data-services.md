---
description: Управление наборами изменений (Master Data Services)
title: Управление наборами изменений
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cc74d46d-7566-45d8-9b51-2cfc262f6abe
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 852396b6c3eb77141e964f1ba72d141153a0badb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471923"
---
# <a name="manage-changesets-master-data-services"></a>Управление наборами изменений (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] можно управлять всеми изменениями по моделям и версиям.  
  
## <a name="prerequisites"></a>Предварительные требования  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** . Дополнительные сведения см. в разделе [разрешения функциональной области &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   Необходимо иметь по крайней мере доступ на чтение сущности или одного из ее атрибутов.  
  
-   Если вы — администратор сущности, вы можете управлять наборами изменений, которые сами создали или которые ожидают утверждения.  
  
-   Если вы не являетесь администратором сущности, вы можете управлять только наборами изменений, которые сами создали.  
  
## <a name="to-manage-the-changesets"></a>Управление наборами изменений  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]выберите модель и версию, а затем нажмите кнопку **Обозреватель**.  
  
2.  Щелкните **Наборы изменений**. Отобразятся все наборы изменений, доступные для управления, для выбранной модели и версии.  
  
3.  Нажмите **Применить** , чтобы просмотреть сведения о наборе изменений.  
  
4.  Нажмите **Удалить** , чтобы удалить набор изменений. Удалить можно только набор изменений, который не находится в состоянии ожидания или утверждения.  
  
5.  Нажмите **Добавить** , чтобы добавить набор изменений.  
  
6.  Нажмите **Изменить** , чтобы изменить набор изменений.  
  
  
