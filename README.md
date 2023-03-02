<div class="row">
    <div class="col-lg-12">
        <div class="card" id="ticketsList">
            <div class="card-header border-0">
                <div class="d-flex align-items-center">
                    <h5 class="card-title mb-0 flex-grow-1">Meetings</h5>
                    <div class="flex-shrink-0">
                        <a data-bs-toggle="modal" data-bs-target="#showModalNew" class="btn btn-danger add-btn">
                            <i class="ri-add-line align-bottom me-1"></i>New Meeting
                        </a>




                        @*<button class="btn btn-secondary" onClick="deleteMultiple()">
                                <i class="ri-delete-bin-2-line"></i>
                            </button>*@
                    </div>
                </div>
            </div>
            <!--<div class="card-body border border-dashed border-end-0 border-start-0">
            <form>
                <div class="row g-3">
                    <div class="col-xxl-5 col-sm-12">
                        <div class="search-box">
                            <input type="text" class="form-control search bg-light border-light"
                                   placeholder="Search for ticket details or something...">
                            <i class="ri-search-line search-icon"></i>
                        </div>
                    </div>-->
            <!--end col-->
            <!--<div class="col-xxl-3 col-sm-4">
                <input type="text" class="form-control bg-light border-light" data-provider="flatpickr"
                       data-date-format="d M, Y" data-range-date="true" id="demo-datepicker"
                       placeholder="Select date range">
            </div>-->
            <!--end col-->
            <!--<div class="col-xxl-3 col-sm-4">
                <div class="input-light">
                    <select class="form-control" data-choices data-choices-search-false
                            name="choices-single-default" id="idStatus">
                        <option value="">Status</option>
                        <option value="all" selected>All</option>
                        <option value="Open">Open</option>
                        <option value="Inprogress">Inprogress</option>
                        <option value="Closed">Closed</option>
                        <option value="New">New</option>
                    </select>
                </div>
            </div>-->
            <!--end col-->
            <!--<div class="col-xxl-1 col-sm-4">
                <button type="button" class="btn btn-primary w-100">
                    <i class="ri-equalizer-fill me-1 align-bottom"></i>
                    Filters
                </button>
            </div>-->
            <!--end col-->
            <!--</div>-->
            <!--end row-->
            <!--</form>
            </div>-->
            <!--end card-body-->
            <div class="card-body border border-dashed border-end-0 border-start-0">
                <div class="table-responsive table-card mb-1 p-3">
                    <table class="table table-hover mb-0" id="ticketTable">
                        <thead>
                            <tr>
                                @*<th scope="col" style="width: 40px;">
                                        <div class="form-check">
                                            <input class="form-check-input" type="checkbox" id="checkAll" value="option">
                                        </div>
                                    </th>*@
                                <th>ID</th>
                                <th>Topic</th>
                                <th>Description</th>
                                <th>Start Time</th>
                                <th>End Time</th>
                                <th>Arranged By</th>

                            </tr>
                        </thead>
                        <tbody class="list form-check-all" id="ticket-list-data">

                            @if (Model.Meetings != null)
                            {


                                @foreach (var meeting in Model.Meetings)
                                {



                                    <tr id="tr_meeting_@meeting.Id">
                                        @*<th scope="row">
                                                <div class="form-check">
                                                    <input class="form-check-input" type="checkbox" name="checkAll" value="option1">
                                                </div>
                                            </th>*@
                                        <td class="id" id="meetingId">@meeting.Id </td>
                                        <td class="Meeting_Name" id="meetingTopic">@meeting.Topic</td>
                                        <td class="Meeting_Description" id="meetingDescription">@meeting.Description</td>
                                        @if (meeting.StartTime != null)
                                        {
                                            <td id="meetingStartTime">@meeting.StartTime</td>

                                        }
                                        else
                                        {
                                            <td>
                                                <a id="meeting_@meeting.Id" onclick="UpdateMeetingStatus(this.id,1)"
                                                   class="btn btn-success">Start Meeting</a>
                                            </td>
                                        }

                                        @if (meeting.EndTime != null && meeting.StartTime != null)
                                        {
                                            <td id="meetingEndTime">@meeting.EndTime</td>
                                        }
                                        else if (meeting.EndTime == null && meeting.StartTime != null)
                                        {
                                            <td>
                                                <a id="meeting_@meeting.Id" onclick="UpdateMeetingStatus(this.id,2)"
                                                   class="btn btn-warning">End Meeting</a>
                                            </td>
                                        }
                                        else
                                        {
                                            <td id="meetingEndTime">Not Started Yet!</td>
                                        }
                                        <td id="meetingCreator">@meeting.Username</td>

                                        @*<td>
                                                <div class="dropdown">
                                                    <button class="btn btn-soft-secondary btn-sm dropdown" type="button"
                                                            data-bs-toggle="dropdown" aria-expanded="false">
                                                        <i class="ri-more-fill align-middle"></i>
                                                    </button>
                                                    <ul class="dropdown-menu dropdown-menu-end">
                                                        <li>
                                                            <a id="meeting_@meeting.Id" class="dropdown-item"
                                                               onclick="OpenMeeting(this.id)">
                                                                <i class="ri-pages-line align-bottom me-2 text-muted"></i> View
                                                            </a>
                                                        </li>
                                                        <li>
                                                            <a id="meeting_@meeting.Id" class="dropdown-item edit-item-btn"
                                                               data-bs-toggle="modal" data-bs-target="#showModalEdit"
                                                               onclick="getValuesOfMeeting(this.id)">
                                                                <i class="ri-pencil-fill align-bottom me-2 text-muted"></i> Edit
                                                            </a>
                                                        </li>
                                                        <li>
                                                            <a id="_meeting_@meeting.Id" href="#deleteOrder"
                                                               class="dropdown-item remove-item-btn" data-bs-toggle="modal"
                                                               onclick="deleteMeeting(this.id)">
                                                                <i class="ri-delete-bin-fill align-bottom me-2 text-muted"></i>
                                                                Delete
                                                            </a>
                                                        </li>
                                                    </ul>
                                                </div>
                                            </td>*@
                                    </tr>

                                }
                            }

                        </tbody>
                    </table>
                    <div class="noresult" style="display: none">
                        <div class="text-center">
                            <lord-icon src="https://cdn.lordicon.com/msoeawqm.json" trigger="loop"
                                       colors="primary:#121331,secondary:#08a88a" style="width:75px;height:75px">
                            </lord-icon>
                            <h5 class="mt-2">Sorry! No Result Found</h5>
                            <p class="text-muted mb-0">
                                We've searched more than 150+ Tickets We did not find any Tickets
                                for you search.
                            </p>
                        </div>
                    </div>
                </div>
                @*<div class="d-flex justify-content-end mt-2">
                        <div class="pagination-wrap hstack gap-2">
                            <a class="page-item pagination-prev disabled" href="#">
                                Previous
                            </a>
                            <ul class="pagination listjs-pagination mb-0"></ul>
                            <a class="page-item pagination-next" href="#">
                                Next
                            </a>
                        </div>
                    </div>*@

                <!-- Modal -->
                <div class="modal fade flip" id="deleteOrder" tabindex="-1" aria-hidden="true">
                    <div class="modal-dialog modal-dialog-centered">
                        <div class="modal-content">
                            <div class="modal-body p-5 text-center">
                                <lord-icon src="https://cdn.lordicon.com/gsqxdxog.json" trigger="loop"
                                           colors="primary:#405189,secondary:#f06548" style="width:90px;height:90px">
                                </lord-icon>
                                <div class="mt-4 text-center">
                                    <h4>You are about to delete a meeting ?</h4>
                                    <p class="text-muted fs-14 mb-4">
                                        Deleting your meeting will remove all of
                                        your information from our database.
                                    </p>
                                    <div class="hstack gap-2 justify-content-center remove">
                                        <button class="btn btn-link link-success fw-medium text-decoration-none"
                                                data-bs-dismiss="modal">
                                            <i class="ri-close-line me-1 align-middle"></i>
                                            Close
                                        </button>
                                        <form asp-controller="Meeting" asp-action="DeleteMeeting" method="post">

                                            <input type="hidden" asp-for="@Model.Id" id="deleteInput">
                                            <button type="submit" class="btn btn-danger" id="delete-record">
                                                Yes, Delete
                                                It
                                            </button>

                                        </form>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <!--end modal -->
            </div>
            <!--end card-body-->
        </div>
        <!--end card-->
    </div>
    <!--end col-->
</div>
<!--end row-->
