# Generative Pages (GenPages) - Official Samples

This file contains links to all official sample pages available in the Microsoft Power Platform Skills repository.

**Main Repository:**  
https://github.com/microsoft/power-platform-skills

**GenPage Plugin Location:**  
https://github.com/microsoft/power-platform-skills/tree/main/plugins/model-apps

**Official Documentation:**  
https://learn.microsoft.com/en-us/power-apps/maker/model-driven-apps/generative-page-external-tools

---

## Official Sample Pages (.tsx)

These are ready-to-use example pages demonstrating different patterns:

| #  | Sample File                          | Description                              | Direct Link |
|----|--------------------------------------|------------------------------------------|-------------|
| 1  | `1-account-grid.tsx`                | Basic account grid view                  | [View](https://github.com/microsoft/power-platform-skills/blob/main/plugins/model-apps/samples/1-account-grid.tsx) |
| 2  | `2-wizard-multi-step.tsx`           | Multi-step wizard form                   | [View](https://github.com/microsoft/power-platform-skills/blob/main/plugins/model-apps/samples/2-wizard-multi-step.tsx) |
| 3  | `3-account-crud-dataverse.tsx`      | Full CRUD operations on Account table    | [View](https://github.com/microsoft/power-platform-skills/blob/main/plugins/model-apps/samples/3-account-crud-dataverse.tsx) |
| 4  | `4-file-upload.tsx`                 | File upload functionality                | [View](https://github.com/microsoft/power-platform-skills/blob/main/plugins/model-apps/samples/4-file-upload.tsx) |
| 5  | `5-navigation-sidebar.tsx`          | Sidebar navigation pattern               | [View](https://github.com/microsoft/power-platform-skills/blob/main/plugins/model-apps/samples/5-navigation-sidebar.tsx) |
| 6  | `6-comprehensive-form.tsx`          | Complex form with multiple controls      | [View](https://github.com/microsoft/power-platform-skills/blob/main/plugins/model-apps/samples/6-comprehensive-form.tsx) |
| 7  | `7-responsive-cards.tsx`            | Responsive card-based layout             | [View](https://github.com/microsoft/power-platform-skills/blob/main/plugins/model-apps/samples/7-responsive-cards.tsx) |
| 8  | `8-dashboard-with-charts.tsx`       | Dashboard with charts (D3 / Fluent)      | [View](https://github.com/microsoft/power-platform-skills/blob/main/plugins/model-apps/samples/8-dashboard-with-charts.tsx) |
| 9  | `9-list-with-caching.tsx`           | List view with data caching              | [View](https://github.com/microsoft/power-platform-skills/blob/main/plugins/model-apps/samples/9-list-with-caching.tsx) |
| 10 | `10-detail-with-pageinput.tsx`      | Detail view using page input parameters  | [View](https://github.com/microsoft/power-platform-skills/blob/main/plugins/model-apps/samples/10-detail-with-pageinput.tsx) |
| 11 | `11-kanban-with-dnd.tsx`            | Kanban board with drag & drop            | [View](https://github.com/microsoft/power-platform-skills/blob/main/plugins/model-apps/samples/11-kanban-with-dnd.tsx) |
| 12 | `12-dialog-form-overlay.tsx`        | Dialog / modal form overlay              | [View](https://github.com/microsoft/power-platform-skills/blob/main/plugins/model-apps/samples/12-dialog-form-overlay.tsx) |

---

## How to Use These Samples

1. Download the desired `.tsx` file.
2. Copy the content into your local `page.tsx`.
3. Update the `--data-sources` and `--prompt` when uploading.
4. Run:
   ```bash
   pac model genpage upload \
     --app-id "Your App" \
     --page-id "existing-guid-or-omit-for-new" \
     --code-file ./page.tsx \
     --data-sources "account,contact" \
     --add-to-sitemap   # only for new pages
   ```

**Tip:** Start with simpler samples (1, 7, 8) and gradually move to more complex ones (3, 11, 12).

---

## Additional Resources

- **Plugin Rules & Guidelines**:  
  https://github.com/microsoft/power-platform-skills/blob/main/plugins/model-apps/references (check for rules.md or genpage rules)

- **Power Platform Skills Main Repo**:  
  https://github.com/microsoft/power-platform-skills

- **GenPage Skill Code**:  
  https://github.com/microsoft/power-platform-skills/tree/main/plugins/model-apps/skills/genpage

These samples follow the official recommended patterns (React 17 + TypeScript + Fluent UI v9 + `dataApi`).

Happy coding!
