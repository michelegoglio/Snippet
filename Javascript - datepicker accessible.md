 ````
  // Create calendar
		jQuery(el).datepicker({
			beforeShow: function () {
				makeAccessible();
			}
		});
		
		function makeAccessible () {
			clearTimeout(makeAccessible.timer);
				
			if (jQuery('.ui-datepicker.ui-widget .ui-datepicker-calendar').is(':visible')) {
								
				// Vars
				var cal = jQuery('.ui-datepicker.ui-widget'),
					cal_grid = cal.find('table'),
					grid_thead = cal_grid.find('thead'),
					grid_thead_tr = grid_thead.find('tr'),
					grid_thead_th = grid_thead.find('th'),
					grid_tbody = cal_grid.find('tbody'),
					grid_tbody_tr = grid_tbody.find('tr'),
					grid_tbody_td = grid_tbody.find('td')
					
				
				// Calendar
				cal.attr('role','region');
					//aria-labelledby="ui-datepicker-1-title"
				
				// Grid
				cal_grid
					.attr('role', 'grid')
					.attr('aria-readonly', true)
					.attr('tabindex', 0);
					//aria-labelledby="ui-datepicker-1-month-lbl"
					//aria-activedescendant="ui-datepicker-1-15"
				
				// THead
				grid_thead.attr('role', 'presentation');
				grid_thead_tr.attr('role', 'row');
				grid_thead_th.each(function () {
					var span_title = jQuery(this).find('span').attr('title');
					jQuery(this)
						.attr('role', 'columnheader')
						.attr('arial-label', span_title)
						.attr('abbr', span_title);
				});
				
				// TBody
				grid_tbody.attr('role', 'presentation');
				grid_tbody_tr.each(function () {
					jQuery(this).attr('role', 'row');
				});
				grid_tbody_td.each(function () {
					var self = jQuery(this),
						self_link = self.find('a');
					
					self
						.attr('role', 'gridcell')
						.attr('aria-selected', false);
					self_link.attr('tabindex', '-1');
				});
			}
			else {
				makeAccessible.timer = setTimeout(makeAccessible, 10);
			}
		}
````
