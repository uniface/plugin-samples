# plugin-samples
IDE Plugin Samples

Samples of custom worksheets for the Uniface 10.3 IDE, similar to those included in <https://community.uniface.com/display/DOW/Uniface+10.3+IDE+Utilities>.

They can be used to explore how IDE add-ins work, or as a basis for adding features or building your own.

## Contents

The supplied plugins currently include the following:
- View Listing
- Checkstyle
- View Statistics

### View Listing (WS_LISTING)

- Shows component compilation listings in an additional tab.
- A rich text edit box is used to display the listing, so search functionality (Ctrl F) is available.

### Checkstyle (WS_CHECKSTYLE)

- Analyzes code and reports standards contraventions.
- The supplied code performs basic changes that entries start with *l* for local proc. You can also check operation names (e.g. *op* prefix) in a similar manner (not enabled by default).
    
### View Statitics (WS_STATISTICS)

- Analyzes and reports lines of code in your component

## Dependencies

- Uses the Uniface meta dictionary (uniface\misc\umeta.xml in the Uniface installation), which is included in the versioned code.
- The Uniface WASListener is required to import WorkArea export files into the repository database and subsequently synchronize them: https://github.com/uniface/WASListener

## Notes

**Warning:** Do not import this version into a Uniface environment other than version 10.3, as the Uniface meta dictionary will differ. Check git branches for your version.

## Development Environment Installation and Configuration

1. Edit the shortcuts and change the Uniface installation location (don't forget to change the /adm switch as well) and working folder if needed
2. Edit your assignment file (e.g. IDE.ASN) if needed (probably not required as paths are relative)
3. Import the source code into your repository using the WAS plugin.
4. Compile the PLUGIN_SAMPLES project using the build shortcut.

## Configuration for use

- Modify the assignment file of your target development environment (e.g. IDE.asn) as follows:

  - Add **PLUGIN-SAMPLES.uar** to the **\[RESOURCES\]** section:

        [RESOURCES]
        .\uar\PLUGIN-SAMPLES.uar

  - Add or modify **[LOGICALS]** to include the desired plug-ins:

        [LOGICALS]
        IDE_DEFINE_WORKSHEETS = WS_LISTING,WS_STATISTICS,WS_CHECKSTYLE

## Licence

MIT
