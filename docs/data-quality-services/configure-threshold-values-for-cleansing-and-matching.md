---
title: Настройка пороговых значений для очистки и сопоставления
description: Узнайте, как настроить пороговые значения, которые будут использоваться при пользовательской очистке и соответствующих действиях в SQL Server Data Quality Services (DQS).
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.admin.config.general.f1
helpviewer_keywords:
- cleansing,threshold value
- cleansing threshold values
- matching,threshold value
ms.assetid: d2305409-7115-45a4-8f60-1213c0a47368
author: swinarko
ms.author: sawinark
ms.openlocfilehash: cfb67f59d7a383d7ca7376c30435462c9a6199d7
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814134"
---
# <a name="configure-threshold-values-for-cleansing-and-matching---data-quality-services-dqs"></a>Настройка пороговых значений для очистки и сопоставления — службы Data Quality Services (DQS)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  В этом разделе описывается настройка пороговых значений, которые будут использоваться в ходе операций автоматизированной очистки и сопоставления в службах [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для настройки этих пороговых значений необходимо иметь роль dqs_administrator в базе данных DQS_MAIN.  
  
##  <a name="configuring-the-threshold-values"></a><a name="Configure"></a> Настройка пороговых значений  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Запустите приложение Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  На главном экране клиента [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] нажмите кнопку **Конфигурация**.  
  
3.  Затем перейдите на вкладку **Общие параметры** . На этой вкладке можно указать пороговые значения для очистки, а также соответствующие действия.  
  
4.  Пороговые значения для операции очистки задаются в следующих полях в области **Интерактивная очистка** :  
  
    -   **Минимальный показатель для предложений**. Минимальная оценка или уровень достоверности, которые будут использоваться службами DQS для предложения значений на замену в ходе автоматизированного процесса очистки. Введите значение в десятичной нотации для соответствующего значения в процентах. Например, введите 0,75 для 75 %. Это значение должно быть меньше или равно значению, указанному в поле **Минимальная оценка для автоматического исправления** . Значение по умолчанию — 0,7.  
  
    -   **Минимальный показатель для автоматического исправления**. Минимальная оценка или уровень достоверности, которые будут использоваться службами DQS для автоматического исправления значений в ходе автоматизированного процесса очистки. Введите значение в десятичной нотации для соответствующего значения в процентах. Например, введите 0,9 для 90 %. Значение по умолчанию — 0,8.  
  
5.  Пороговое значение для операции сопоставления задается в поле **Минимальная оценка для записи** в области **Сопоставление** . Это значение задает минимальную оценку для записи, которая позволяет считать ее соответствующей другой записи. Значение по умолчанию — 80 %.  
  
6.  Щелкните **Закрыть**.  
  
  
