# AppFlowy Cloud REST API — лавлах

!!! warning "Энэ хуудсанд юу баталгаатай, юу биш вэ"
    Энд зөвхөн AppFlowy-ийн албан ёсны OpenAPI баримтын индекс хүснэгтэд **шууд харагдаж байсан** мэдээлэл (класс, метод, HTTP хүсэлт, тайлбар, зам дахь параметрийн нэр, нэвтрэлтийн төрөл) орсон. Параметрийн төрөл, хариуны схем, алдааны код зэргийг би уншиж чадаагүй тул _баталгаажаагүй_ гэж тэмдэглэсэн. Таамаглаж бөглөөгүй. Эдгээрийг OpenAPI YAML/JSON-оос шалгаж бөглөнө үү (доорх "Бөглөх заавар").

## Хамрах хүрээ ба эх сурвалж

| Зүйл | Утга |
|---|---|
| API | AppFlowy Cloud REST API (клиент апп биш, серверийн API) |
| Эх сурвалж | [OpenAPI README](https://github.com/AppFlowy-IO/documentations/blob/main/documentation/appflowy-cloud/openapi/README.md) |
| Хандсан огноо | 2026-10-19 (`main` салбар; тодорхой commit/tag тэмдэглэгдээгүй) |
| Base URL | `https://beta.appflowy.cloud` (баримтад "All URIs are relative to" гэж заасан). Self-hosted орчинд өөрийн серверийн URL ашиглана. |
| Нэвтрэлт | `BearerAuth` — HTTP Bearer Token (JWT) |
| Хувилбар/edition | _баталгаажаагүй_ — managed cloud болон self-hosted-д ижил эсэхийг шалгаагүй |

**Урьдчилсан нөхцөл:** хүчинтэй JWT access token, хандах workspace-ийн гишүүн эрх. Token авах нь баримтын `gotrueToken_request` / `gotrue_token_response` моделиудтай холбоотой бололтой боловч схемийг уншаагүй тул _баталгаажаагүй_.

## Endpoint-ийн хураангуй

| Нэр | Метод | Зам |
|---|---|---|
| [`getWorkspaces`](#getworkspaces) | `GET` | `/api/workspace` |
| [`getWorkspaceFolder`](#getworkspacefolder) | `GET` | `/api/workspace/{workspace_id}/folder` |
| [`getDatabases`](#getdatabases) | `GET` | `/api/workspace/{workspace_id}/database` |
| [`getDatabaseFields`](#getdatabasefields) | `GET` | `/api/workspace/{workspace_id}/database/{database_id}/fields` |
| [`getDatabaseRowIds`](#getdatabaserowids) | `GET` | `/api/workspace/{workspace_id}/database/{database_id}/row` |
| [`getDatabaseRowDetails`](#getdatabaserowdetails) | `GET` | `/api/workspace/{workspace_id}/database/{database_id}/row/detail` |
| [`createDatabaseRow`](#createdatabaserow) | `POST` | `/api/workspace/{workspace_id}/database/{database_id}/row` |
| [`upsertDatabaseRow`](#upsertdatabaserow) | `PUT` | `/api/workspace/{workspace_id}/database/{database_id}/row` |

## `getWorkspaces`

- **Зорилго:** Бүх workspace-ийн жагсаалтыг авна ("Retrieves a list of all workspaces").
- **Хувилбар/боломж:** _баталгаажаагүй_
- **Урьдчилсан нөхцөл:** Base URL, `Authorization: Bearer <ACCESS_TOKEN>`
- **HTTP хүсэлт:** `GET /api/workspace`

| Параметр | Байрлал | Төрөл | Заавал эсэх | Анхдагч | Тайлбар |
|---|---|---|---:|---|---|
| — | — | — | — | — | Замд параметр байхгүй. Query параметр байгаа эсэх: _баталгаажаагүй_ |

- **Амжилттай хариу:** `getWorkspaces_200_response` (статус код: _баталгаажаагүй_)
- **Алдаа:** _баталгаажаагүй_ — доорх [алдааны хүснэгт](#errors)-ийг үзнэ үү
- **Жишээ:** хүсэлтийн хэлбэр нь дээрх зам ба Bearer нэвтрэлтээс гарсан бөгөөд **ажиллуулж баталгаажуулаагүй**:

```bash
curl -X GET "https://beta.appflowy.cloud/api/workspace" \
  -H "Authorization: Bearer <ACCESS_TOKEN>"
```

- **Холбоотой заавар:** [Хуудас хуваалцах](../how-to/share-a-page.md)
- **Эх сурвалж:** [OpenAPI README](https://github.com/AppFlowy-IO/documentations/blob/main/documentation/appflowy-cloud/openapi/README.md)

## `getWorkspaceFolder`

- **Зорилго:** Workspace-ийн folder эсвэл дэд folder-ыг авна ("Retrieves workspace folder or subfolder").
- **Хувилбар/боломж:** _баталгаажаагүй_
- **Урьдчилсан нөхцөл:** Base URL, `Authorization: Bearer <ACCESS_TOKEN>`
- **HTTP хүсэлт:** `GET /api/workspace/{workspace_id}/folder`

| Параметр | Байрлал | Төрөл | Заавал эсэх | Анхдагч | Тайлбар |
|---|---|---|---:|---|---|
| `workspace_id` | path | _баталгаажаагүй_ | тийм (замын хэсэг) | байхгүй | Workspace-ийн танигч |

- **Амжилттай хариу:** `getWorkspaceFolder_200_response` (статус код: _баталгаажаагүй_)
- **Алдаа:** _баталгаажаагүй_ — доорх [алдааны хүснэгт](#errors)-ийг үзнэ үү
- **Жишээ:** хүсэлтийн хэлбэр нь дээрх зам ба Bearer нэвтрэлтээс гарсан бөгөөд **ажиллуулж баталгаажуулаагүй**:

```bash
curl -X GET "https://beta.appflowy.cloud/api/workspace/<WORKSPACE_ID>/folder" \
  -H "Authorization: Bearer <ACCESS_TOKEN>"
```

- **Холбоотой заавар:** [Анхны төслийн Board](../tutorials/first-project-board.md)
- **Эх сурвалж:** [OpenAPI README](https://github.com/AppFlowy-IO/documentations/blob/main/documentation/appflowy-cloud/openapi/README.md)

## `getDatabases`

- **Зорилго:** Workspace доторх мэдээллийн сангуудын жагсаалтыг авна.
- **Хувилбар/боломж:** _баталгаажаагүй_
- **Урьдчилсан нөхцөл:** Base URL, `Authorization: Bearer <ACCESS_TOKEN>`
- **HTTP хүсэлт:** `GET /api/workspace/{workspace_id}/database`

| Параметр | Байрлал | Төрөл | Заавал эсэх | Анхдагч | Тайлбар |
|---|---|---|---:|---|---|
| `workspace_id` | path | _баталгаажаагүй_ | тийм (замын хэсэг) | байхгүй | Workspace-ийн танигч |

- **Амжилттай хариу:** `getDatabases_200_response` (статус код: _баталгаажаагүй_)
- **Алдаа:** _баталгаажаагүй_ — доорх [алдааны хүснэгт](#errors)-ийг үзнэ үү
- **Жишээ:** хүсэлтийн хэлбэр нь дээрх зам ба Bearer нэвтрэлтээс гарсан бөгөөд **ажиллуулж баталгаажуулаагүй**:

```bash
curl -X GET "https://beta.appflowy.cloud/api/workspace/<WORKSPACE_ID>/database" \
  -H "Authorization: Bearer <ACCESS_TOKEN>"
```

- **Холбоотой заавар:** [Board харагдац үүсгэх](../how-to/create-a-board-view.md)
- **Эх сурвалж:** [OpenAPI README](https://github.com/AppFlowy-IO/documentations/blob/main/documentation/appflowy-cloud/openapi/README.md)

## `getDatabaseFields`

- **Зорилго:** Сонгосон мэдээллийн сангийн талбаруудын (fields) жагсаалтыг авна.
- **Хувилбар/боломж:** _баталгаажаагүй_
- **Урьдчилсан нөхцөл:** Base URL, `Authorization: Bearer <ACCESS_TOKEN>`
- **HTTP хүсэлт:** `GET /api/workspace/{workspace_id}/database/{database_id}/fields`

| Параметр | Байрлал | Төрөл | Заавал эсэх | Анхдагч | Тайлбар |
|---|---|---|---:|---|---|
| `workspace_id` | path | _баталгаажаагүй_ | тийм (замын хэсэг) | байхгүй | Workspace-ийн танигч |
| `database_id` | path | _баталгаажаагүй_ | тийм (замын хэсэг) | байхгүй | Мэдээллийн сангийн танигч |

- **Амжилттай хариу:** `баталгаажаагүй` (статус код: _баталгаажаагүй_)
- **Алдаа:** _баталгаажаагүй_ — доорх [алдааны хүснэгт](#errors)-ийг үзнэ үү
- **Жишээ:** хүсэлтийн хэлбэр нь дээрх зам ба Bearer нэвтрэлтээс гарсан бөгөөд **ажиллуулж баталгаажуулаагүй**:

```bash
curl -X GET "https://beta.appflowy.cloud/api/workspace/<WORKSPACE_ID>/database/<DATABASE_ID>/fields" \
  -H "Authorization: Bearer <ACCESS_TOKEN>"
```

- **Холбоотой заавар:** [Board харагдац үүсгэх](../how-to/create-a-board-view.md) (бүлэглэх Status талбар)
- **Эх сурвалж:** [OpenAPI README](https://github.com/AppFlowy-IO/documentations/blob/main/documentation/appflowy-cloud/openapi/README.md)

## `getDatabaseRowIds`

- **Зорилго:** Сонгосон мэдээллийн сангийн мөрүүдийн id-ийн жагсаалтыг авна.
- **Хувилбар/боломж:** _баталгаажаагүй_
- **Урьдчилсан нөхцөл:** Base URL, `Authorization: Bearer <ACCESS_TOKEN>`
- **HTTP хүсэлт:** `GET /api/workspace/{workspace_id}/database/{database_id}/row`

| Параметр | Байрлал | Төрөл | Заавал эсэх | Анхдагч | Тайлбар |
|---|---|---|---:|---|---|
| `workspace_id` | path | _баталгаажаагүй_ | тийм (замын хэсэг) | байхгүй | Workspace-ийн танигч |
| `database_id` | path | _баталгаажаагүй_ | тийм (замын хэсэг) | байхгүй | Мэдээллийн сангийн танигч |

- **Амжилттай хариу:** `баталгаажаагүй` (статус код: _баталгаажаагүй_)
- **Алдаа:** _баталгаажаагүй_ — доорх [алдааны хүснэгт](#errors)-ийг үзнэ үү
- **Жишээ:** хүсэлтийн хэлбэр нь дээрх зам ба Bearer нэвтрэлтээс гарсан бөгөөд **ажиллуулж баталгаажуулаагүй**:

```bash
curl -X GET "https://beta.appflowy.cloud/api/workspace/<WORKSPACE_ID>/database/<DATABASE_ID>/row" \
  -H "Authorization: Bearer <ACCESS_TOKEN>"
```

- **Холбоотой заавар:** [Анхны төслийн Board](../tutorials/first-project-board.md) (даалгаврын карт = мөр)
- **Эх сурвалж:** [OpenAPI README](https://github.com/AppFlowy-IO/documentations/blob/main/documentation/appflowy-cloud/openapi/README.md)

## `getDatabaseRowDetails`

- **Зорилго:** Сонгосон мэдээллийн сангийн мөрүүдийн дэлгэрэнгүйг авна.
- **Хувилбар/боломж:** _баталгаажаагүй_
- **Урьдчилсан нөхцөл:** Base URL, `Authorization: Bearer <ACCESS_TOKEN>`
- **HTTP хүсэлт:** `GET /api/workspace/{workspace_id}/database/{database_id}/row/detail`

| Параметр | Байрлал | Төрөл | Заавал эсэх | Анхдагч | Тайлбар |
|---|---|---|---:|---|---|
| `workspace_id` | path | _баталгаажаагүй_ | тийм (замын хэсэг) | байхгүй | Workspace-ийн танигч |
| `database_id` | path | _баталгаажаагүй_ | тийм (замын хэсэг) | байхгүй | Мэдээллийн сангийн танигч |

- **Амжилттай хариу:** `баталгаажаагүй` (статус код: _баталгаажаагүй_)
- **Алдаа:** _баталгаажаагүй_ — доорх [алдааны хүснэгт](#errors)-ийг үзнэ үү
- **Жишээ:** хүсэлтийн хэлбэр нь дээрх зам ба Bearer нэвтрэлтээс гарсан бөгөөд **ажиллуулж баталгаажуулаагүй**:

```bash
curl -X GET "https://beta.appflowy.cloud/api/workspace/<WORKSPACE_ID>/database/<DATABASE_ID>/row/detail" \
  -H "Authorization: Bearer <ACCESS_TOKEN>"
```

- **Холбоотой заавар:** [Анхны төслийн Board](../tutorials/first-project-board.md)
- **Эх сурвалж:** [OpenAPI README](https://github.com/AppFlowy-IO/documentations/blob/main/documentation/appflowy-cloud/openapi/README.md)

## `createDatabaseRow`

- **Зорилго:** Сонгосон мэдээллийн санд шинэ мөр үүсгэнэ.
- **Хувилбар/боломж:** _баталгаажаагүй_
- **Урьдчилсан нөхцөл:** Base URL, `Authorization: Bearer <ACCESS_TOKEN>`
- **HTTP хүсэлт:** `POST /api/workspace/{workspace_id}/database/{database_id}/row`

| Параметр | Байрлал | Төрөл | Заавал эсэх | Анхдагч | Тайлбар |
|---|---|---|---:|---|---|
| `workspace_id` | path | _баталгаажаагүй_ | тийм (замын хэсэг) | байхгүй | Workspace-ийн танигч |
| `database_id` | path | _баталгаажаагүй_ | тийм (замын хэсэг) | байхгүй | Мэдээллийн сангийн танигч |
| _(body)_ | body | _баталгаажаагүй_ | _баталгаажаагүй_ | _баталгаажаагүй_ | Мөрийн өгөгдөл |

- **Амжилттай хариу:** `баталгаажаагүй` (статус код: _баталгаажаагүй_)
- **Алдаа:** _баталгаажаагүй_ — доорх [алдааны хүснэгт](#errors)-ийг үзнэ үү
- **Жишээ:** хүсэлтийн хэлбэр нь дээрх зам ба Bearer нэвтрэлтээс гарсан бөгөөд **ажиллуулж баталгаажуулаагүй**:

```bash
curl -X POST "https://beta.appflowy.cloud/api/workspace/<WORKSPACE_ID>/database/<DATABASE_ID>/row" \
  -H "Authorization: Bearer <ACCESS_TOKEN>"
```

- **Холбоотой заавар:** [Анхны төслийн Board](../tutorials/first-project-board.md) (5-р алхам: даалгавар нэмэх)
- **Эх сурвалж:** [OpenAPI README](https://github.com/AppFlowy-IO/documentations/blob/main/documentation/appflowy-cloud/openapi/README.md)

## `upsertDatabaseRow`

- **Зорилго:** Сонгосон мэдээллийн санд мөрийг шинэчилнэ, байхгүй бол үүсгэнэ (upsert). Хүсэлтийн модел: `upsert_database_row`, хариу: `upsertDatabaseRow_200_response`.
- **Хувилбар/боломж:** _баталгаажаагүй_
- **Урьдчилсан нөхцөл:** Base URL, `Authorization: Bearer <ACCESS_TOKEN>`
- **HTTP хүсэлт:** `PUT /api/workspace/{workspace_id}/database/{database_id}/row`

| Параметр | Байрлал | Төрөл | Заавал эсэх | Анхдагч | Тайлбар |
|---|---|---|---:|---|---|
| `workspace_id` | path | _баталгаажаагүй_ | тийм (замын хэсэг) | байхгүй | Workspace-ийн танигч |
| `database_id` | path | _баталгаажаагүй_ | тийм (замын хэсэг) | байхгүй | Мэдээллийн сангийн танигч |
| _(body)_ | body | `upsert_database_row` | _баталгаажаагүй_ | _баталгаажаагүй_ | Мөрийн өгөгдөл (моделийн талбарууд _баталгаажаагүй_) |

- **Амжилттай хариу:** `upsertDatabaseRow_200_response` (статус код: _баталгаажаагүй_)
- **Алдаа:** _баталгаажаагүй_ — доорх [алдааны хүснэгт](#errors)-ийг үзнэ үү
- **Жишээ:** хүсэлтийн хэлбэр нь дээрх зам ба Bearer нэвтрэлтээс гарсан бөгөөд **ажиллуулж баталгаажуулаагүй**:

```bash
curl -X PUT "https://beta.appflowy.cloud/api/workspace/<WORKSPACE_ID>/database/<DATABASE_ID>/row" \
  -H "Authorization: Bearer <ACCESS_TOKEN>"
```

- **Холбоотой заавар:** [Board харагдац үүсгэх](../how-to/create-a-board-view.md) (картын Status өөрчлөх)
- **Эх сурвалж:** [OpenAPI README](https://github.com/AppFlowy-IO/documentations/blob/main/documentation/appflowy-cloud/openapi/README.md)

## Алдааны мэдээлэл {#errors}

| Алдаа/статус | Эх сурвалжид баримтжсан шалтгаан | Зөвлөх үйлдэл |
|---|---|---|
| _баталгаажаагүй_ | _баталгаажаагүй_ | Эхлээд token хүчинтэй эсэх, workspace-д эрхтэй эсэхийг шалгана. Эдгээр нь баримтжаагүй тул таамаглал гэдгийг анхаарна. |

## Бөглөх заавар (үлдсэн _баталгаажаагүй_ талбарууд)

1. OpenAPI YAML/JSON-г нээж, endpoint бүрийн `parameters`, `requestBody`, `responses` хэсгийг хуулна.
2. Өөрийн workspace дээр (эсвэл туршилтын self-hosted серверт) амжилттай болон алдаатай (token буруу, workspace_id буруу) хүсэлт илгээж, статус код, хариуг тэмдэглэнэ.
3. Бодит token, workspace id-г баримтад **хэзээ ч** бүү оруул.
4. Баталгаажсан мэдээллийг `_баталгаажаагүй_` гэсний оронд шивнэ.

!!! info "Хэрэв энэ API хүрээ таны даалгаварт тохирохгүй бол"
    Багшаасаа AppFlowy Cloud-ийн REST API нь Week 07-ын "public API" шаардлагад тохирох эсэхийг асууна. Зарим эх сурвалж (гуравдагч этгээдийн SDK, MCP төслүүд) нийтийн OpenAPI-д ороогүй endpoint-ууд (жишээ нь page-view) байдаг гэж тэмдэглэсэн. Тэдгээрийг албан ёсны гэж үзэхгүй.
