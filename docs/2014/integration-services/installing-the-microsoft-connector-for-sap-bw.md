---
title: Установка Microsoft Connector 1.1 для SAP BW | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: dc6bbbf5972615880d3852d5f56a955862c9f22b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194306"
---
# <a name="installing-the-microsoft-connector-for-11-sap-bw"></a>Установка Microsoft Connector 1.1 для SAP BW
  Чтобы установить [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 для SAP BW и сопутствующую документацию, загрузите и запустите пакет установщика Windows из SQL Server с пакетом обновления веб-страницы компонентов.  
  
> [!IMPORTANT]  
>  Документация по Microsoft Connector 1.1 для SAP BW предполагает, что читатель знаком со средой SAP Netweaver BW. Дополнительные сведения о SAP Netweaver BW или сведения о настройке объектов и процессов SAP Netweaver BW см. в документации SAP.  
  
> [!IMPORTANT]  
>  Для извлечения данных из SAP Netweaver BW требуется дополнительная лицензия SAP. Обратитесь к SAP, чтобы уточнить требования.  
  
## <a name="required-sap-files"></a>Необходимые файлы SAP  
 Для использования [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 для SAP BW, не нужно устанавливать программное обеспечение SAP внешнего интерфейса (SAP GUI) на локальном компьютере.  
  
 Однако необходимо скопировать файл соединителя SAP .NET (librfc32.dll) во вложенную папку в системном каталоге Windows. (Обычно это каталог **C:\Windows\system32**.)  
  
## <a name="considerations-for-64-bit-computers"></a>Замечания для 64-разрядных компьютеров  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 для SAP BW полностью поддерживает 64-разрядной версии [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows. На 64-разрядном компьютере [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 для SAP BW имеет следующие дополнительные требования:  
  
-   Для запуска пакетов в 64-разрядном режиме в любой 64-разрядной ОС Windows скопируйте 64-разрядную версию файла графического пользовательского интерфейса SAP librfc32.dll в папку **system32** в каталоге Windows. (Обычно это каталог **C:\Windows\system32**.)  
  
-   Для запуска пакетов в 32-разрядном режиме в любой 64-разрядной ОС Windows скопируйте файл графического пользовательского интерфейса SAP librfc32.dll в папку **SysWow64** в каталоге Windows. (Обычно это каталог **C:\Windows\SysWow64**.)  
  
  