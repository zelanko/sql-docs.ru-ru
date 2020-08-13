---
title: Пример использования поставщика Azure Key Vault с поддержкой Always Encrypted с безопасными анклавами | Документация Майкрософт
ms.custom: ''
ms.date: 07/09/2020
ms.reviewer: v-kaywon
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: karinazhou
ms.author: v-jizho2
ms.openlocfilehash: d97d32ba50255181ae21cf0a1ac1cd079092b122
ms.sourcegitcommit: 7ce4a81c1b91239c8871c50f97ecaf387f439f6c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217762"
---
# <a name="example-demonstrating-use-of-azure-key-vault-provider-with-always-encrypted-enabled-with-secure-enclaves"></a>Пример использования поставщика Azure Key Vault с поддержкой Always Encrypted с безопасными анклавами

[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly.md)]

[!INCLUDE [appliesto-netfx-netcore-xxxx-md](../../../includes/appliesto-netfx-netcore-xxxx-md.md)]

В этом примере демонстрируется использование поставщика Azure Key Vault при доступе к зашифрованным столбцам.

[!code-csharp [Azure Key Vault Provider with Enclave Example#1](~/../sqlclient/doc/samples/AzureKeyVaultProviderWithEnclaveProviderExample.cs#1)]

> [!NOTE]
> Always Encrypted с безопасными анклавами поддерживается только в Windows.

## <a name="see-also"></a>См. также:

- [Пример использования поставщика Azure Key Vault с поддержкой Always Encrypted](azure-key-vault-example.md)
- [Руководство. Разработка приложения .NET с помощью Always Encrypted с безопасными анклавами](tutorial-always-encrypted-enclaves-develop-net-apps.md)
- [Использование Always Encrypted с поставщиком данных Microsoft .NET для SQL Server](sqlclient-support-always-encrypted.md)
