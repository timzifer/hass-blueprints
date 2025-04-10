# Home Assistant Blueprint: Purge History by Label (Daily)

This Blueprint provides an automation that periodically purges the history (`recorder` data) for entities assigned a specific label within Home Assistant. It runs once daily at a fixed time (default: 3:05 AM).

This is useful because the standard `recorder` component does not allow excluding entities based on labels.

**Warning:** Purging history data is **irreversible**. Use this Blueprint with caution and ensure you are targeting the correct label. Frequent purging of large amounts of data might also impact system performance during the purge operation.

## Blueprint Inputs

| Input         | Description                                                                                                | Selector        | Default        |
|---------------|------------------------------------------------------------------------------------------------------------|-----------------|----------------|
| `target_label`| The label assigned to entities whose history should be purged. **(Case-sensitive!)** | `text`          | (None)         |
| `keep_days`   | (Optional) Number of recent days of history to **KEEP**. Set to `0` to purge **ALL** history for the entities. | `number` (days) | `0` (Purge all)|

*(Note: The execution time is currently fixed within the Blueprint trigger at `03:05:00`. You can edit the Blueprint file to change this time if needed.)*

## How to Use

1.  **Import the Blueprint:**
    * Click the Import Blueprint button below:

      [![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Ftimzifer%2Fhass-blueprints%2Fmain%2Fpurge_history_by_label_daily.yaml)
      *(Assumes the file is located at the root of the `main` branch)*

    * Or, manually import by going to **Settings > Automations & Scenes > Blueprints** in Home Assistant, click **Import Blueprint**, and paste the following URL:
      ```
      [https://raw.githubusercontent.com/timzifer/hass-blueprints/main/purge_history_by_label_daily.yaml](https://raw.githubusercontent.com/timzifer/hass-blueprints/main/purge_history_by_label_daily.yaml)
      ```

2.  **Create an Automation:**
    * Go to **Settings > Automations & Scenes > Blueprints**.
    * Find the "Purge History by Label (Daily)" Blueprint and click **Create Automation**.
    * **Target Label:** Enter the exact name of the label you want to use for purging (e.g., `no_history`).
    * **Keep Recent Days:** Enter the number of days to keep, or leave at `0` to purge all history for the labeled entities.
    * Save the automation.

## Source URL (for Updates)

The following `source_url:` should be included within the Blueprint YAML file itself. This allows Home Assistant to check for updates when you manually trigger a re-import via the UI.

```yaml
# source_url: [https://raw.githubusercontent.com/timzifer/hass-blueprints/main/purge_history_by_label_daily.yaml](https://raw.githubusercontent.com/timzifer/hass-blueprints/main/purge_history_by_label_daily.yaml)
```
*(Ensure this URL inside your actual Blueprint file is correct)*

## License

This Blueprint is provided under the MIT License. See the [LICENSE](LICENSE) file for details.
