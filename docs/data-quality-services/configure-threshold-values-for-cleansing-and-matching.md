---
title: Настройка пороговых значений для очистки и сопоставления | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology:
- data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.admin.config.general.f1
helpviewer_keywords:
- cleansing,threshold value
- cleansing threshold values
- matching,threshold value
ms.assetid: d2305409-7115-45a4-8f60-1213c0a47368
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a04fbc0b19b59097c46a7e55ecbd55030f4e68b0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47733588"
---
# <a name="configure-threshold-values-for-cleansing-and-matching"></a>Настройка пороговых значений для очистки и сопоставления

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В этом разделе описывается настройка пороговых значений, которые будут использоваться в ходе операций автоматизированной очистки и сопоставления в службах [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Для настройки этих пороговых значений необходимо иметь роль dqs_administrator в базе данных DQS_MAIN.  
  
##  <a name="Configure"></a> Настройка пороговых значений  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Запуск клиентского приложения Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  На главном экране клиента [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] нажмите кнопку **Конфигурация**.  
  
3.  Далее щелкните вкладку **Общие параметры** . На этой вкладке можно задать пороговые значения для операций очистки и сопоставления.  
  
4.  Пороговые значения для операции очистки задаются в следующих полях в области **Интерактивная очистка** :  
  
    -   **Минимальный показатель для предложений**. Минимальная оценка или уровень достоверности, которые будут использоваться службами DQS для предложения значений на замену в ходе автоматизированного процесса очистки. Введите значение в десятичной нотации для соответствующего значения в процентах. Например, введите 0,75 для 75 %. Это значение должно быть меньше или равно значению, указанному в поле **Минимальная оценка для автоматического исправления** . Значение по умолчанию — 0,7.  
  
    -   **Минимальный показатель для автоматического исправления**. Минимальная оценка или уровень достоверности, которые будут использоваться службами DQS для автоматического исправления значений в ходе автоматизированного процесса очистки. Введите значение в десятичной нотации для соответствующего значения в процентах. Например, введите 0,9 для 90 %. Значение по умолчанию — 0,8.  
  
5.  Пороговое значение для операции сопоставления задается в поле **Минимальная оценка для записи** в области **Сопоставление** . Это значение задает минимальную оценку для записи, которая позволяет считать ее соответствующей другой записи. Значение по умолчанию — 80 %.  
  
6.  Щелкните **Закрыть**.  
  
  
