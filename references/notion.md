# Notion filing

This package ships no personal workspace links, IDs, or configured destination.
Read [setup](setup.md) before the first write.

## Plain page or categorized database

Plain-page mode: create one child page under the verified target; keep metadata
in its body. Use the actual title parameter supported by the current connector.

Database mode: use the verified data source, not the containing page ID. Map
logical fields to the actual schema. Preserve existing property types and data.

Suggested starter fields, only for an authorized new database:

| Logical field | Suggested name | Type |
| --- | --- | --- |
| title | 名称 / Name | Title |
| category | 主分类 / Category | Select |
| tags | 标签 / Tags | Multi-select |
| source_type | 来源类型 / Source type | Select |
| source_url | 来源链接 / Source URL | URL |
| processed_date | 整理日期 / Processed date | Date |

Source type options may be Podcast, Video, Social post, Article, Book excerpt,
Other, or the user's existing equivalents. Do not guess a publication date.

For requested topic columns, create a board grouped by the category field.
Where supported, add per-category filtered views and an all-notes view.
Read the connector's current view DSL/schema; never guess undocumented options.
Some boards hide empty groups: disclose that behavior or add empty category tabs.
A view name alone does not prove that its filter works.

Creating a database does not authorize migrating unrelated notes. If the user
requests a migration, inventory the affected pages, preserve their identities,
content, images, and action states, and verify coverage before declaring success.

## Category decisions

Use one main category and 1–3 tags; do not duplicate the page across topics.
The supplied template offers these editable categories:

| Category | Scope |
| --- | --- |
| 心理 / Psychology | Emotions, cognition, relationship psychology, self-understanding |
| 哲学 / Philosophy | Meaning, ethics, values, reasoning, philosophical ideas |
| 经济理财 / Economics & finance | Budgets, income, consumption, investing, economics |
| 健康 / Health | Sleep, movement, nutrition, physical health, clinical information |
| 成长学习 / Learning & growth | Learning methods, careers, skills, habits, productivity |
| 科技工具 / Technology & tools | AI, software, technical trends, tool workflows |
| 生活方式 / Lifestyle | Everyday life, travel, home, interests, aesthetics |
| 待分类 / Unsorted | No confident fit in the user's taxonomy |

Classify by the problem solved, not an isolated word. For example, a video using
philosophical questions to practice English belongs in Learning & growth.
Respect user-selected categories. When adding tags, preserve all existing options;
do not create new top-level categories without a user request or agreement.

## Write procedure

1. Fetch target and current schema; read the connector's Markdown specification.
2. Search/query the destination for the source URL/canonical ID plus excerpt range.
   Follow pagination when needed. A truncated search is not exhaustive deduplication.
3. Read matching records. Skip complete duplicates; update when useful new
   material exists, preserving user notes and checklist state. Ask if identity
   is ambiguous. Do not overwrite simply because titles are similar.
4. Look for a few genuinely related records within this collection. Cite only
   verified page links; omit links when no useful match exists.
5. Prepare complete content before creating a record. Set known metadata and
   actual schema properties. These notes are not executable Notion skills.
6. Upload authorized images through the connector's supported flow, then embed
   its returned file source in the same note. Keep credentials/signed URLs out
   of public files and logs. If upload fails, save the authorized text and report
   the separate image failure; do not claim the image is attached.
7. For async operations, wait for success, then fetch the result. Verify parent/
   data source, title, category, content, image, source, and action checklist.
8. After an uncertain create, inspect the destination before retrying. Do not
   create duplicates. Retry once only after verifying it did not succeed and
   the failure is recoverable; otherwise report the unconfirmed state.

Do not broaden sharing, permissions, or publication as part of saving.
