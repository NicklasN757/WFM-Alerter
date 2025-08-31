# WFM-Alerter (Warframe Market Alerter)
This project began while some friends and I were playing Warframe. 
I noticed that the unofficial market lacked a way to notify players when desired in-game items became available at a specific price. 
This tool allows users to set up alerts for items they want and receive email notifications when those items are listed at or below their specified price.

To use it, simply deploy the project to an Azure Function App after adding the necessary configurations. It currently supports email notifications via SMTP, but could be extended to support other notification methods.

I host this privately for a few friends, so please don’t expect a fully managed service. If you’d like to use it, feel free to deploy your own instance.

## Getting Started 
1. Clone the repository.
2. Restore NuGet packages.
3. Add missing configuration files (host.json, local.settings.json) as described in this [README](./WFM-Alerter.App/readme.md).
4. Build and run the project using Visual Studio 2022 or the .NET CLI.

**For deployment to Azure:**

Create an Azure Function App in the Azure Portal, then publish the project from Visual Studio or use the Azure CLI. 
For the mail communication service, just follow the instructions here [Microsoft Learn](https://learn.microsoft.com/en-us/azure/communication-services/quickstarts/email/create-email-communication-resource?pivots=platform-azp)

The total hosting cost should be minimal, as Azure Functions use a pay-as-you-go pricing model. However, costs may vary depending on the number of emails sent, your region, and other factors. My personal cost is around 1 euro per month for just under 100 emails sent.

## Usage 
- Add an alert: Send a POST request to `/addalert` with item details.
- Delete an alert: Send a DELETE request to `/deletealert/{alertId}`.
- List alerts: Send a GET request to `/getalerts`.
- Alerts are checked every 5 minutes; notifications are sent via email.

## API Reference 
- `GET /getalerts`: Returns all alerts.
- `POST /addalert`: Adds a new alert (JSON payload).
- `DELETE /deletealert/{alertId}`: Deletes an alert by ID.
- All endpoints return JSON responses.

## Testing 
For API testing, use Postman or similar tools with provided endpoints. 

Postman test collection can be found here: [WFM-Alerter-API.postman_collection.json](./Tests/WFM-Alerter-API.postman_collection.json)

## Contributing 
Thanks for checking out WFM-Alerter! This project is open source under the GPL-3.0 license, which means you're free to:

- Fork the repository
- Modify the code
- Use it in your own projects

While direct code contributions (e.g. pull requests) are currently not accepted, issues are welcome! Feel free to:

- Report bugs
- Suggest features
- Ask questions

Your feedback helps improve the project and guide future updates.

## License 
GPL-3.0 License. See [LICENSE](LICENSE.txt) for details.

## Acknowledgments 
Special thanks to the Warframe Market community and Digital Extremes (DE) for creating the amazing game Warframe and fostering such a vibrant community!