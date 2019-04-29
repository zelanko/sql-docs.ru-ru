---
title: Диспетчер подключений подписки Azure | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpsubscrconn.f1
- sql11.dts.designer.afpsubscrconn.f1
ms.assetid: e1225327-c308-4c50-8f44-c411f52ef378
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6ea90d10a0228321d33a4c55076e9ed46a14c80c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833496"
---
# <a name="azure-subscription-connection-manager"></a>Диспетчер подключений подписки Azure
  Диспетчер подключений Azure HDInsight позволяет пакету служб SSIS для подключения к подписке Azure, используя значения, указываемые для свойств: идентификатора подписки Azure и сертификата управления.  
  
1.  В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите **Подписка Azure**и щелкните **Добавить**.  Отобразится следующее диалоговое окно **Azure Subscription Connection Manager Editor** (Редактор диспетчера подключений подписки Azure).  
  
     ![SSIS AzureSubscriptionManager](../media/ssis-azuresubscriptionmanager.png "AzureSubscriptionManager служб SSIS")  
  
2.  Введите уникальный идентификатор подписки Azure, который идентифицирует подписку Azure, в поле **Идентификатор подписки Azure**.  Значение можно найти на [портале управления Azure](https://manage.windowsazure.com) на странице **Параметры** .  
  
     ![SSIS-AzureSettings-SubscriptionID](../media/ssis-azuresettings-subscriptionid.png "SSIS-AzureSettings-SubscriptionID")  
  
3.  В раскрывающихся списках выберите значения **Расположение хранилища сертификатов управления** и **Имя хранилища сертификатов управления** .  
  
4.  Введите значение **Отпечаток сертификата управления** или щелкните **Обзор…** и выберите сертификат из выбранного хранилища. Сертификат должен быть передан как сертификат управления для подписки. Чтобы сделать это, нажмите кнопку **Отправить** на следующей странице портала Azure (см. эту [запись MSDN](https://msdn.microsoft.com/library/azure/gg551722.aspx) для получения дополнительных сведений).  
  
     ![SSIS-AzureSettings-ManagementCertificate](../media/ssis-azuresettings-managementcertificate.png "SSIS-AzureSettings-ManagementCertificate")  
  
5.  Нажмите кнопку **Проверить подключение** для проверки подключения.  
  
6.  Чтобы закрыть диалоговое окно, нажмите кнопку **ОК** .  
  
  
