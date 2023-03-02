$(document).ready(function () {
            var table = $('#ticketTable').DataTable({
                dom: 'QB<rf<t>lip>',
                lengthMenu: [10, 25, 50, 75, 100],
                select: {
                    style: 'single',
                    toggleable: true
                },
                buttons: [
                    {
                        text: 'View',
                        className: 'btn-primary',
                        action: function () {
                            if (table.rows({ selected: true }).count() != 0) {
                                let meetingId = table.rows({ selected: true }).data().toArray()[0][0];
                                window.open('/Meeting/Meeting?Id=' + meetingId, "_blank");
                            }
                        }
                    },
                    {
                        text: 'Edit',
                        className: 'btn-warning',
                        action: function () {
                            if (table.rows({ selected: true }).count() != 0) {
                                let meetingId = table.rows({ selected: true }).data().toArray()[0][0];
                                let meetingName = table.rows({ selected: true }).data().toArray()[0][1];
                                let meetingDescription = table.rows({ selected: true }).data().toArray()[0][2];
                                document.getElementById("meetingId-field").value = meetingId;
                                document.getElementById("meetingTopic-field").value = meetingName;
                                document.getElementById("meetingDescription-field").value = meetingDescription;
                                $('#showModalEdit').modal('show');
                            }
                        }
                    },
                    {
                        text: 'Delete',
                        className: 'btn-danger',
                        action: function () {
                            if (table.rows({ selected: true }).count() != 0) {
                                var Id = table.rows({ selected: true }).data().toArray()[0][0];
                                document.getElementById("deleteInput").value = Id;
                                let button = document.getElementById("delete-record");
                                button.setAttribute("onclick", "DelMeetingNote();");
                                $('#deleteOrder').modal('show');
                            }
                        }
                    },
                    {
                        text: 'Participants',
                        className: 'btn-info',
                        action: function () {
                            if (table.rows({ selected: true }).count() != 0) {
                                $("#userList-field").html(cloneUserList.clone());
                                var Id = table.rows({ selected: true }).data().toArray()[0][0];
                                GetParticipants(Id);
                                document.getElementById("meetingIdSpan").innerText = Id;
                                $('#modalParticipants').modal('show');
                            }
                        }
                    },
                    {
                        extend: 'collection',
                        text: 'Export',
                        className: 'btn-secondary',
                        buttons: [
                            'copy',
                            'excel',
                            'csv',
                            'pdf',
                            'print'
                        ]
                    }
                ]
            });
        });
