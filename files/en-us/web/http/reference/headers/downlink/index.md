---
title: Downlink header
short-title: Downlink
slug: Web/HTTP/Reference/Headers/Downlink
page-type: http-header
status:
  - experimental
browser-compat: http.headers.Downlink
sidebar: http
---

{{SeeCompatTable}}

The HTTP **`Downlink`** {{Glossary("request header")}} is used in [Client Hints](/en-US/docs/Web/HTTP/Guides/Client_hints) to provide the approximate bandwidth in Mbps of the client's connection to the server.

The hint allows a server to choose what information is sent based on the network bandwidth.
For example, a server might choose to send smaller versions of images and other resources on low bandwidth networks.

> [!NOTE]
> The {{HTTPHeader("Vary")}} header is used in responses to indicate that a different resource is sent for every different value of the header (see [HTTP Caching Vary](/en-US/docs/Web/HTTP/Guides/Caching#vary)).
> Even if `Downlink` is used to configure what resources are sent, consider omitting it in the {{HTTPHeader("Vary")}} header — it is likely to change often, which effectively makes the resource uncacheable.

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">Header type</th>
      <td>
        {{Glossary("Request header")}},
        <a href="/en-US/docs/Web/HTTP/Guides/Client_hints">Client hint</a>
      </td>
    </tr>
    <tr>
      <th scope="row">{{Glossary("Forbidden request header")}}</th>
      <td>No</td>
    </tr>
  </tbody>
</table>

## Syntax

```http
Downlink: <number>
```

## Directives

- `<number>`
  - : The downlink rate in Mbps, rounded to the nearest 25 kilobits.
    The downlink rate may be used as a {{glossary("fingerprinting")}} variable, so values for the header are intentionally coarse to reduce the potential for its misuse.

## Examples

A server first needs to opt in to receive the `Downlink` header by sending the {{HTTPHeader("Accept-CH")}} response header containing `Downlink`.

```http
Accept-CH: Downlink
```

Then on subsequent requests the client might send a `Downlink` header back:

```http
Downlink: 1.7
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Improving user privacy and developer experience with User-Agent Client Hints](https://developer.chrome.com/docs/privacy-security/user-agent-client-hints) (developer.chrome.com)
- Network client hints
  - {{HTTPHeader("RTT")}}
  - {{HTTPHeader("ECT")}}
  - {{HTTPHeader("Save-Data")}}
- {{HTTPHeader("Accept-CH")}}
- [HTTP Caching: Vary](/en-US/docs/Web/HTTP/Guides/Caching#vary) and {{HTTPHeader("Vary")}}
- {{domxref("NetworkInformation.effectiveType")}}
