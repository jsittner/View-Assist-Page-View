# View-Assist

Page view uses an input_text to hide and unhide cards using automation calls.

Requirements for using page view on View-Assist

1. Create a text input helper for each dashboard  

    input_text.viewscreen_page


2. Add a 'page_view' attribute to the template sensor

    page_view: "input_text.viewscreen_page"



The automation changes the visibility of the different cards.

Automation parts:

    service: input_text.set_value
    data:
    value: clock
    target:
    entity_id: "{{ target_display_page_view }}"


Visibility parts:

    visibility:
        - condition: or
        conditions:
            - condition: state
            entity: input_text.viewscreen_page
            state: clock
            - condition: state
            entity: input_text.viewscreen_page
            state: all    
