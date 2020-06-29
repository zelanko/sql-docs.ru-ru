---
title: Установка соединителя Microsoft для 1,1 SAP BW | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a4362773ab6e0ec0252062d1695a921e7054226
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85424751"
---
# <a name="installing-the-microsoft-connector-for-11-sap-bw"></a>Установка Microsoft Connector 1.1 для SAP BW
  Чтобы установить [!INCLUDE[msCoName](../includes/msconame-md.md)] соединитель 1,1 для SAP BW и его документацию, скачайте и запустите пакет установщика Windows на веб-странице SQL Server пакета дополнительных компонентов.  
  
> [!IMPORTANT]  
>  Документация по Microsoft Connector 1.1 для SAP BW предполагает, что читатель знаком со средой SAP Netweaver BW. Дополнительные сведения о SAP Netweaver BW или сведения о настройке объектов и процессов SAP Netweaver BW см. в документации SAP.  
  
> [!IMPORTANT]  
>  Для извлечения данных из SAP Netweaver BW требуется дополнительная лицензия SAP. Обратитесь к SAP, чтобы уточнить требования.  
  
## <a name="required-sap-files"></a>Необходимые файлы SAP  
 Чтобы использовать [!INCLUDE[msCoName](../includes/msconame-md.md)] соединитель 1,1 для SAP BW, не нужно устанавливать клиентское программное обеспечение SAP (графический интерфейс SAP) на локальном компьютере.  
  
 Однако необходимо скопировать файл соединителя SAP .NET (librfc32.dll) во вложенную папку в системном каталоге Windows. (Обычно это каталог **C:\Windows\system32**.)  
  
## <a name="considerations-for-64-bit-computers"></a>Замечания для 64-разрядных компьютеров  
 [!INCLUDE[msCoName](../includes/msconame-md.md)]Соединитель 1,1 для SAP BW полностью поддерживает 64-разрядную версию [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows. На 64-разрядном компьютере [!INCLUDE[msCoName](../includes/msconame-md.md)] соединитель 1,1 для SAP BW имеет следующие дополнительные требования:  
  
-   Для запуска пакетов в 64-разрядном режиме в любой 64-разрядной ОС Windows скопируйте 64-разрядную версию файла графического пользовательского интерфейса SAP librfc32.dll в папку **system32** в каталоге Windows. (Обычно это каталог **C:\Windows\system32**.)  
  
-   Для запуска пакетов в 32-разрядном режиме в любой 64-разрядной ОС Windows скопируйте файл графического пользовательского интерфейса SAP librfc32.dll в папку **SysWow64** в каталоге Windows. (Обычно это каталог **C:\Windows\SysWow64**.)  
  
  
