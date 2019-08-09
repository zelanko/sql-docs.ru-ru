---
title: Настройка журналов ошибок SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql13.swb.configurelogs.configureerrorlogs.f1
ms.assetid: 03f0d463-9b0b-4af9-a853-da936d75e5af
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a4da039e1fcc41570fcead275bbe4b2cb0be5797
ms.sourcegitcommit: 0d89bcaebdf87db3bd26db2ca263be9c671b0220
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2019
ms.locfileid: "68731100"
---
# <a name="scm-services---configure-sql-server-error-logs"></a>Службы SCM. Настройка журналов ошибок SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описано, как просмотреть и изменить способ очистки журналов ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  

## <a name="to-open-the-configure-sql-server-error-logs-dialog-box"></a>Открытие диалогового окна «Настройка журналов ошибок SQL Server»  

1. В обозревателе объектов разверните экземпляр SQL Server, раскройте узел **Управление**, щелкните правой кнопкой мыши **Журналы SQL Server**, а затем выберите пункт **Настройка**.

2. В диалоговом окне **Настройка журналов ошибок SQL Server** выберите один из следующих параметров.

    A. Число файлов журнала

      **Ограничить количество файлов журнала ошибок перед очисткой**

      Установите этот флажок, чтобы ограничить количество файлов журнала ошибок, создаваемых до их очистки. При каждом запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создается новый журнал ошибок. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сохраняет резервные копии шести предыдущих журналов, если этот флажок не установлен и ниже не указано иное максимальное число файлов журнала ошибок.  
  
      **Максимальное количество файлов журналов ошибок**

      Укажите максимальное количество файлов журнала ошибок, создаваемых до их очистки. Значение по умолчанию — 6, то есть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сохраняет шесть предыдущих резервных копий журналов до их очистки.

    Б. Размер файла журнала

      **Максимальный размер файла журнала ошибок в КБ**

      Можно задать размер каждого файла в килобайтах. Если оставить значение 0, размер журнала будет неограничен.
