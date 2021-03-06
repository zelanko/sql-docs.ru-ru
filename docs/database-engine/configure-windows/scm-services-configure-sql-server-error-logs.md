---
title: Настройка журналов ошибок SQL Server | Документы Майкрософт
description: Ознакомьтесь с очисткой журнала ошибок. Узнайте, как задать максимальный размер файла журнала и число предыдущих файлов журнала для резервного копирования и архивации в SQL Server.
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 060b3828c772a030ab095ae1bea857dc8eaa3b5a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85651378"
---
# <a name="scm-services---configure-sql-server-error-logs"></a>Службы SCM. Настройка журналов ошибок SQL Server

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  В этом разделе описано, как просмотреть и изменить способ очистки журналов ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  

## <a name="to-open-the-configure-sql-server-error-logs-dialog-box"></a>Открытие диалогового окна «Настройка журналов ошибок SQL Server»  

1. В обозревателе объектов разверните экземпляр SQL Server, раскройте узел **Управление**, щелкните правой кнопкой мыши **Журналы SQL Server**, а затем выберите пункт **Настройка**.

2. В диалоговом окне **Настройка журналов ошибок SQL Server** выберите один из следующих параметров.

    а. Число файлов журнала

      **Ограничить количество файлов журнала ошибок перед очисткой**

      Установите этот флажок, чтобы ограничить количество файлов журнала ошибок, создаваемых до их очистки. При каждом запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создается новый журнал ошибок. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сохраняет резервные копии шести предыдущих журналов, если этот флажок не установлен и ниже не указано иное максимальное число файлов журнала ошибок.  
  
      **Максимальное количество файлов журналов ошибок**

      Укажите максимальное количество архивированных файлов журнала ошибок, создаваемых до их очистки. Значение по умолчанию — 6, не включая текущий. Это значение определяет число предыдущих резервных копий журналов, которые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранит, прежде чем их очистить.

    b. Размер файла журнала

      **Максимальный размер файла журнала ошибок в КБ**

      Можно задать размер каждого файла в килобайтах. Если оставить значение 0, размер журнала будет неограничен.
