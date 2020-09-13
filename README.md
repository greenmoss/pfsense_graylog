This is a set of extractors for use within Graylog, to parse the output of
Pfsense filter logs.

# Installation
* Open the Graylog administrative interface
* Open the "System/Inputs" menu
* Select "Inputs"
* Select "Manage Extractors" for the input that receives Pfsense logs
* Select "Actions" menu
* Select "Import extractors"
* Paste the contents of [extractors.json](extractors.json) into the text box
* Select the button "Add extractors to input"

# Usage
* Open your Graylog search
* Search for `pfsense_common_log_data`
* The search results should now be showing all TCP/UDP/ICMP data as separate fields

# Background
This is intended to be a complete implementation of the Pfsense [BNF output
format](https://docs.netgate.com/pfsense/en/latest/monitoring/raw-filter-log-format.html#bnf-grammar).
Note that a few of the icmp return types are *not* yet implemented, due to me
not yet having example traffic to test them against!

I tried a few other sets of Graylog content packs and extractors. However the
ones I tried had a lot of embedded regexp and pattern duplication. This caused
them to miss multiple pfsense filter messages.

The rules in this repository are instead intended to parse as much as possible.
This allows them to be easily extended further, should the specifications
evolve. This also makes it less likely for an overly-specific rule to
completely miss parsing an entire pfsense log line.

These extractors generate a lot of extra/intermediate fields. This may be
overly verbose, or it may aid in debugging/extending, depending on your point
of view.

