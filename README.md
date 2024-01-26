# Creator Roles for EPrints
Adding creator roles to an EPrints repository using the [CRediT](https://www.casrai.org/credit.html) taxonomy.  

## EPServices Fork

The `eprintug` plugin [creators_roles](https://github.com/eprintsug/creators_roles) has been forked by EPServices to translate into an ingredient format and structure.

### Versions & Compatability

| EPrints Version | creators_roles Version | Tested | Production |
| ----------- | ----------- | ----------- | ----------- |
| [3.4.5](https://github.com/eprints/eprints3.4/releases/tag/v3.4.5) | [Initial Fork v0.0.1-alpha](https://github.com/eprints/creators_roles/releases/tag/v0.0.1-alpha) | ✅ | ❌ |

### Improvements & Issues

#### Current EPrints Versions (>3.4.5)

- #1
- Investigate different styling
- Investigate searching over this field
- POSSIBLE BUG: When editing a record which has roles attributed to a creator as a user who cannot view this field. I suppose it's because the new creator DS does not contain the field values for the role sub field. Can you do a partial update of a compound field? OR should we show the field and make it readonly like the orcid advance plugin?
- Investigate accessibility

#### Future EPrints Versions

- How can this ingredient be made availanle for both versions of EPRints simlutaniously & should it be?
- JSON field to use new metafield (relies on new feature)
- Bootstrap integration
- eprints_classic_style integration

## Installation Instructions

> These instructions are valid for EPrints v3.4.5

1. Install the ingredient in the `/opt/eprints3/ingredients` directory.

	```bash
 	cd /opt/eprints3/ingredients/
	git clone https://github.com/eprints/creators_roles.git
 	```

2. Enable to ingredient in the relevant flavour `inc` file

	> example shown for publications flavour `pub_lib`.

	**Edit** this file `/opt/eprints3/flavours/pub_lib/inc`

 	**Add** this line
	```bash
	ingredients/creators_roles
	```

3. Add this to the compound field for creators:

	```perl
	{
		sub_name => 'credit_roles',
		type => 'CreditRole',
		input_cols => 1,
		allow_null => 1,
		input_cols => 25
	}
	```

4. Regenerate your static files to include the javascript needed for the custom control:

	```bash
	$ bin/generate_static [your repository name]
	```

5. Enable editing of the credit role by adding `credit_role:edit` to the appropriate role in user_roles.pl or adding as a user permission.

## Developer Credits

### Initial Developers:

[Micheal Eadie](https://github.com/MickEadie), University of Glasgow  
[Liam Green-Hughes](https://github.com/leg20-unikent), University of Kent  

### EPServices Fork Developers:
[Edward Oakley](https://github.com/fatchild), EPrints Services
