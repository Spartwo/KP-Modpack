## SimpleFuelSwitch configuration

### Configs provided with the mod

There are currently three config files provided here:

* Add_LFO_to_LF_tanks.cfg:  Every LFO tank has an option added for an equivalent amount of LF.
* Add_LF_to_LFO_tanks.cfg:  For certain specific LF tanks, add LFO as an option.
* Hide_redundant_parts.cfg:  Some parts are no longer needed, because the function is filled by another tank that can now switch resources. Remove these, to reduce parts tab clutter in the editor.

Note that the "removed" parts from the third config file aren't _actually_ removed, just hidden.  Thus, any existing ships you've already designed or launched with them will be fine.

If you don't like what any of the above files do (e.g. "Oh noes, I don't want to get rid of the 'redundant' parts" or whatever), you can just delete any or all of them.


### How to tinker with your own config

SimpleFuelSwitch is fairly simple to configure, by design. There are two new PartModules to deal with:

* ModuleSimpleFuelSwitch
* ModuleSwitchableResources

For a part to use these modules, it should be set up as follows:

1. If the part has any "built-in" resources that you want to be switchable, _remove them_. (They'll be replaced by these new modules.)
2. Add _one_ ModuleSimpleFuelSwitch. (Don't add multiple ones.)
3. Add one ModuleSwitchableResources for each resource option you want to have. Generally you'll always have at least two of these (otherwise there's nothing to "switch").

Example:  You want to modify a monoprop tank to be able to choose between monoprop and LFO. You'd use ModuleManager to patch it as follows:

1. Delete the monoprop from the part (since these modules will take over).
2. Add a ModuleSimpleFuelSwitch.
3. Add one ModuleSwitchableResources for the monoprop option, and another ModuleSwitchableResources for the LFO option.

Each ModuleSwitchableResources can specify the following:

* _resourcesId_: *Required.* A unique ID field that distinguishes this ModuleSwitchableResources from all the others on this part. Never displayed to a user.
* _displayName_: How you want it to show up in the UI (e.g. "LFO"). Optional. If you don't specify, will be auto-generated from the resource names.
* _selectorFieldName_: How you want the button in the UI to be labeled, e.g. "Fuel Type". Optional; if unspecified, defaults to "Resource".
* _isDefault_: Whether you want _this_ set of resources to be the one that's initially picked by default for newly placed parts.
* Resources.

The "resourcesId" field can have any value you want (ideally would be something human-readable, to facilitate debugging).  It needs to meet two requirements:

* Unique within the part: don't add two ModuleSwitchableResources that have the same resourceId as each other.
* Permanently invariant: once you've used it to design and launch ships, you can never change it after that, because doing so would break any existing ships that used the old ID.

The resources for the ModuleSwitchableResources are specified in a set of RESOURCE sections, same as resources for a regular part.


### Using variants

SimpleFuelSwitch also supports the ability to set up config that ties specific resource selections to _variants_, i.e. picking different variants will select different resource types.

The default configs that are installed with this mod don't happen to use the feature. If you'd like to see how it works, though, please see the "examples" folder on the mod's github repository for some ideas.

Executive summary is that all you have to do is add a "linkedVariant" field to each of your ModuleSwitchableResources, specifying which variant (or variants) correspond to that resource selection.
