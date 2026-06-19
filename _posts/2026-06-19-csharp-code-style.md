---
layout: post
title: C# code conventions
---

La convention est la suivante :



Sur l'IDE Rider, il faut modifier le fichier `.editorconfig` à la racine du projet.

Un exemple de `.editorconfig` :

```editorconfig
root = true

[*.cs]

indent_style = space
indent_size = 2
tab_width = 2

charset = utf-8
end_of_line = lf
insert_final_newline = true
trim_trailing_whitespace = true

max_line_length = 100

csharp_using_directive_placement = outside_namespace:warning

dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = false

csharp_new_line_before_open_brace = none

csharp_new_line_before_else = false
csharp_new_line_before_catch = false
csharp_new_line_before_finally = false

csharp_new_line_before_members_in_object_initializers = false
csharp_new_line_before_members_in_anonymous_types = false
csharp_new_line_between_query_expression_clauses = false

csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_block_contents = true
csharp_indent_braces = false

csharp_space_after_keywords_in_control_flow_statements = true

dotnet_style_operator_placement_when_wrapping = beginning_of_line
csharp_space_around_binary_operators = before_and_after

csharp_space_after_cast = false

csharp_space_between_method_declaration_parameter_list_parentheses = false
csharp_space_between_method_call_parameter_list_parentheses = false
csharp_space_between_parentheses = false
csharp_space_before_open_square_brackets = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_square_brackets = false
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_after_comma = true
csharp_space_before_comma = false
csharp_space_after_dot = false
csharp_space_before_dot = false
csharp_space_after_semicolon_in_for_statement = true
csharp_space_before_semicolon_in_for_statement = false

csharp_preserve_single_line_statements = false
csharp_preserve_single_line_blocks = true

dotnet_naming_rule.interface_should_begin_with_i.severity = warning
dotnet_naming_rule.interface_should_begin_with_i.symbols = interface
dotnet_naming_rule.interface_should_begin_with_i.style = begins_with_i
dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_style.begins_with_i.required_prefix = I
dotnet_naming_style.begins_with_i.capitalization = pascal_case

dotnet_naming_rule.types_should_be_pascal_case.severity = warning
dotnet_naming_rule.types_should_be_pascal_case.symbols = types
dotnet_naming_rule.types_should_be_pascal_case.style = pascal_case_style
dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum, namespace, delegate
dotnet_naming_style.pascal_case_style.capitalization = pascal_case

dotnet_naming_rule.public_members_should_be_pascal_case.severity = warning
dotnet_naming_rule.public_members_should_be_pascal_case.symbols = public_members
dotnet_naming_rule.public_members_should_be_pascal_case.style = pascal_case_style
dotnet_naming_symbols.public_members.applicable_kinds = property, method, field, event
dotnet_naming_symbols.public_members.applicable_accessibilities = public, protected, internal, protected_internal

dotnet_naming_rule.private_fields_should_be_camel_case.severity = warning
dotnet_naming_rule.private_fields_should_be_camel_case.symbols = private_fields
dotnet_naming_rule.private_fields_should_be_camel_case.style = underscore_camel_case
dotnet_naming_symbols.private_fields.applicable_kinds = field
dotnet_naming_symbols.private_fields.applicable_accessibilities = private
dotnet_naming_style.underscore_camel_case.required_prefix = _
dotnet_naming_style.underscore_camel_case.capitalization = camel_case

dotnet_naming_rule.locals_should_be_camel_case.severity = warning
dotnet_naming_rule.locals_should_be_camel_case.symbols = locals
dotnet_naming_rule.locals_should_be_camel_case.style = camel_case_style
dotnet_naming_symbols.locals.applicable_kinds = parameter, local
dotnet_naming_style.camel_case_style.capitalization = camel_case

csharp_style_var_for_built_in_types = false:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = false:suggestion

dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion

dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion

csharp_style_expression_bodied_methods = when_on_single_line:suggestion
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion

csharp_prefer_braces = true:warning

dotnet_style_require_accessibility_modifiers = omit_if_default:silent
csharp_preferred_modifier_order = public, protected, internal, private, new, abstract, virtual, override, sealed, static, readonly, extern, unsafe, volatile, async:warning
```

Sur IntelliJ en Java, ce sera un fichier XML à fournir, par exemple : https://google.github.io/styleguide/intellij-java-google-style.xml

## Sources:

- https://google.github.io/styleguide/csharp-style.html
- https://google.github.io/styleguide/javaguide.html
- https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/code-style-rule-options
