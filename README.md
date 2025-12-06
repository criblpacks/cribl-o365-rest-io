# O365 Rest Collector IO
----

## About this Pack

## About this Pack

This pack is built as a complete SOURCE + DESTINATION solution (identified by the IO suffix). Data collection and delivery happen entirely within the pack's context, eliminating the need to connect it to globally defined Sources and Destinations. 

This pack is designed to handle JSON data collected from the Office 365 Message Trace collector source. The JSON is parsed and the timestamp normalized from the proper field within each event. 

The pack includes three forms of outputs:
- Normalized JSON.
- OCSF - Primarily meant for Amazon Security Lake, the pack normalizes the data into the proper OCSF category.
- Splunk - default index and sourcetype supplied from Knowledge > Variables, but can be overwritten in pipeline.

## Deployment

* This pack is configured by default to use the Worker Group's *Default Destination*.
* To use the *Default Destination*: No changes are required. The pack will route the data to the destination currently set as the Default on the Worker Group.
* To use a different Destination: You must update the pack's routes to specify your desired Destination.
* For immediate functionality without requiring Pack route filter expression modifications, every bundled Source within this pack adds a hidden field: `__packsource`. This field allows for seamless routing based on the Pack source.

### Configure Source(s)

Configure the *Office 365 Message Trace Source*, detailed instructions for configuring the source can be found at [Cribl's Github](https://github.com/criblio/Cribl-Microsoft/blob/main/KnowledgeArticles/O365AppRegistrationForCribl/O365-AppRegistration_for_Cribl.md) or [official documentation](https://docs.cribl.io/stream/sources-office365-msg-trace/).

Navigate to Knowledge > Variables and update the following with the appropriate values:
- `o365_tenant_id`: Your Office365 Tenant ID
- `o365_client_id`: Your Office365 Client ID

Navigate to Source > Office 365 > Message Trace > Authentication and update the `Client Secret` for the connection. 

### Configure Reductions and Output Format

* Data can be configured to output data in either OCSF or normalized JSON (Splunk) format - enable *only one* format!
* This pack includes several functions that can help reduce events. Please make sure you evaluate the functions before enabling, to ensure vital data is not missed. 

### Configure your Destination/Update Pack Routes
To ensure proper data routing, you must make a choice: retain the current setting to use the Default Destination defined by your Worker Group, or define a new Destination directly inside this pack and adjust the pack's route accordingly.

### Commit and Deploy
Once everything is configured, perform a Commit & Deploy to enable data collection.


## Upgrades

Upgrading certain Cribl Packs using the same Pack ID can have unintended consequences. See [Upgrading an Existing Pack](https://docs.cribl.io/stream/packs#upgrading) for details.

## Release Notes

### Version 1.1.0
- Pack sources are now mostly configured via variables.

### Version 1.0.0
- Initial release

## Contributing to the Pack

To contribute to the Pack, please connect with us on [Cribl Community Slack](https://cribl-community.slack.com/). You can suggest new features or offer to collaborate.

## License
This Pack uses the following license: [Apache 2.0](https://github.com/criblio/appscope/blob/master/LICENSE).